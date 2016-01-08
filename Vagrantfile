HOST_NUMBER=3
HOST_PREFIX="fjammes"


required_plugins = %w{
  vagrant-openstack-provider
  vagrant-hostmanager
}

plugins_to_install = required_plugins.select { |plugin| not Vagrant.has_plugin? plugin }
if not plugins_to_install.empty?
  puts "Installing plugins: #{plugins_to_install.join(' ')}"
  system "vagrant plugin install #{plugins_to_install.join(' ')}"
  exec "vagrant #{ARGV.join(' ')}"
end

def n_slaves
    (1..HOST_NUMBER)
end

Vagrant.configure('2') do |config|
  config.ssh.username = 'ubuntu'
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = false
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  config.hostmanager.ip_resolver = proc do |vm, resolving_vm|
    if floating_ip = (vm.ssh_info && vm.ssh_info[:host])
      private_ip_line = `vagrant ssh -c 'ip route get 1' #{vm.name}`.split("\n").first
      private_ip = private_ip_line.split.last
      puts "Add entry: #{private_ip} #{vm.name}"
      private_ip
    end
  end
  n_slaves.each do |slave_id|
    slave = "#{HOST_PREFIX}-qserv-#{slave_id}"
    config.vm.define slave do |define|
      define.vm.hostname = "#{slave}"
      define.vm.provider :openstack do |provider, override|
        provider.image = 'e6a3a7fb-10a2-47e0-a19a-d40e17821100'
      end
  end
end

  config.vm.provider :openstack do |os,override|
    os.sync_method        = 'none'
    os.username           = ENV['OS_USERNAME']
    os.password           = ENV['OS_PASSWORD']
    os.tenant_name        = ENV['OS_PROJECT_NAME']
    os.openstack_auth_url = ENV['OS_AUTH_URL']
    os.flavor             = 'r1.medium'
    os.floating_ip_pool   = 'ext-net'
    os.networks           = 'fc77a88d-a9fb-47bb-a65d-39d1be7a7174'
    os.security_groups    = ['default', 'remote SSH']
  end
end
