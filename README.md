# vagrant
 	
1.vagrant up default detect hyperv, need to add --provider virtualbox. 

2.vagrant not support virtualbox 5.2 

## useage
vagrant box add .\Centos7php7.box --name Centos7php7

## then
vagrant up --provider virtualbox

## About the version Follow the specifications to avoid compatibility problems

 vagrant -v
```
Vagrant 2.0.0
```
centos7 version
```
[root@localhost ~]# uname -a
Linux localhost.localdomain 3.10.0-229.el7.x86_64 #1 SMP Fri Mar 6 11:36:42 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[root@localhost ~]# cat /etc/redhat-release 
CentOS Linux release 7.1.1503 (Core) 
[root@localhost ~]# cat /proc/version 
Linux version 3.10.0-229.el7.x86_64 (builder@kbuilder.dev.centos.org) (gcc version 4.8.2 20140120 (Red Hat 4.8.2-16) (GCC) ) #1 SMP Fri Mar 6 11:36:42 UTC 2015
```
VirtualBox version
```
 5.0.40 r115130
```
host system
```
Win10
```
VBoxGuestAdditions
```
[root@localhost ~]# VBoxService -V
5.0.0r101573

```