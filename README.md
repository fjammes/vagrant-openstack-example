example
==

download LSST-openrc.sh from https://nebula.ncsa.illinois.edu/

`Access & Security` -> `API Access` -> `Download OpenStack RC File`

    source LSST-openrc.sh
    <input nebula pasword>

```
$ vagrant status
Current machine states:

docker-1                  not created (openstack)
docker-2                  not created (openstack)
docker-3                  not created (openstack)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
$ vagrant up docker-1
Bringing machine 'docker-1' up with 'openstack' provider...
==> docker-1: Finding flavor for server...
==> docker-1: Finding image for server...
==> docker-1: Finding network(s) for server...
==> docker-1: Launching a server with the following settings...
==> docker-1:  -- Tenant          : LSST
==> docker-1:  -- Name            : docker-1
==> docker-1:  -- Flavor          : r1.medium
==> docker-1:  -- FlavorRef       : 9608fe5f-7804-4a9f-b481-8e8b252b02c7
==> docker-1:  -- Image           : ubuntu-15.04-jacek-docker-1
==> docker-1:  -- ImageRef        : e6a3a7fb-10a2-47e0-a19a-d40e17821100
==> docker-1:  -- KeyPair         : vagrant-generated-v56px46x
==> docker-1:  -- Network         : fc77a88d-a9fb-47bb-a65d-39d1be7a7174
==> docker-1: Waiting for the server to be built...
==> docker-1: Using floating IP 141.142.208.191
==> docker-1: Waiting for SSH to become available...
Connection to 141.142.208.191 closed.
==> docker-1: The server is ready!
==> docker-1: Sync folders are disabled in the provider configuration
$ vagrant ssh docker-1
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-32-generic x86_64)
...
ubuntu@docker-1:~$ exit
logout
Connection to 141.142.208.191 closed.
$ vagrant status
Current machine states:

docker-1                  active (openstack)
docker-2                  not created (openstack)
docker-3                  not created (openstack)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
[master] ~/github/qserv-openstack-examples/vagrant-openstack-example $ vagrant destroy -f docker-1
==> docker-1: Deleting server...
==> docker-1: Waiting for the server to be deleted...
$ vagrant status
Current machine states:

docker-1                  not created (openstack)
docker-2                  not created (openstack)
docker-3                  not created (openstack)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.

```
