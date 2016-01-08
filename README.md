example
==

# Install vagrant

```
wget https://releases.hashicorp.com/vagrant/1.7.4/vagrant_1.7.4_x86_64.deb
su -c 'dpkg -i vagrant_1.7.4_x86_64.deb'
```

# Log in

download LSST-openrc.sh from https://nebula.ncsa.illinois.edu/

`Access & Security` -> `API Access` -> `Download OpenStack RC File`

    source LSST-openrc.sh
    <input nebula pasword>

# Monitor and start VM

```
$ vagrant status

$ vagrant up docker-1
$ vagrant ssh docker-1
$ vagrant status
```

# Configure ssh client

```
(echo && vagrant ssh-config) >> ~/.ssh/config
```
