## Install and Initial Server Setup,


### Register the copy,

`[root@rhel-92-04-vagrantbox ~]# subscription-manager register --username <$INSERT_USERNAME_HERE> --password <$INSERT_PASSWORD_HERE>`

`[root@rhel-92-04-vagrantbox ~]# insights-client --register`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager register --username <username> --password <password> --auto-attach`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager list --available --all`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager refresh`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager remove --all`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager unregister`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager clean`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager register`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager auto-attach`

`[root@rhel-92-04-vagrantbox ~]# subscription-manager attach`


### Extra package,

`[root@rhel-92-04-vagrantbox ~]# sudo subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms`

`[root@rhel-92-04-vagrantbox ~]# sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm`


### Update the system,

`[root@rhel-92-04-vagrantbox ~]# sudo yum update`


### Static ip,

`[root@rhel-92-04-vagrantbox ~]# nmtui`


### Hostnames,

`[root@rhel-92-04-vagrantbox ~]# sudo nano /etc/hosts`

`[root@rhel-92-04-vagrantbox ~]# sudo nano /etc/hostname`


### Users,

`[root@rhel-92-04-vagrantbox ~]# adduser`

`[root@rhel-92-04-vagrantbox ~]# passwd`

`[root@rhel-92-04-vagrantbox ~]# usermod -aG wheel anup`

`[root@rhel-92-04-vagrantbox ~]# visudo`

`[root@rhel-92-04-vagrantbox ~]# id anup`


### SSH authentication,

`[root@rhel-92-04-vagrantbox ~]# ssh-keygen -t rsa -b 4096`

`[root@rhel-92-04-vagrantbox ~]# ls -ltr .ssh/`

`[root@rhel-92-04-vagrantbox ~]# ssh-copy-id root@192.168.56.161`


### Update the system again,

`[root@rhel-92-04-vagrantbox ~]# sudo yum update`


### Development Tools,

`[root@rhel-92-04-vagrantbox ~]# yum groupinstall "Development Tools"`
