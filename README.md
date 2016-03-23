example
==

# Pre-requisites

## Install vagrant

```
$ wget https://releases.hashicorp.com/vagrant/1.7.4/vagrant_1.7.4_x86_64.deb
$ su -c 'dpkg -i vagrant_1.7.4_x86_64.deb'
```

## Log in OpenStack cloud

download LSST-openrc.sh from https://nebula.ncsa.illinois.edu/

`Access & Security` -> `API Access` -> `Download OpenStack RC File`

    source LSST-openrc.sh
    <input nebula password>

# Monitor and start VM

```
$ ln -s Vagrantfile.ncsa Vagrantfile
$ vagrant up
$ vagrant status
```

# Update /etc/hosts on all VM

```
$ vagrant hostmanager
```

# Configure ssh client

Update you ssh client configuration manually, or
by using next command:
```
(echo && vagrant ssh-config) >> ~/.ssh/config
```
