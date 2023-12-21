### AlmaLinux OS : https://almalinux.org/get-almalinux/


### Platform,

`anup@almalinux-9-204:~$ cat /etc/os-release`

`anup@almalinux-9-204:~$ hostnamectl`


### System Information,

`anup@almalinux-9-204:~$ uname -a`


### Resources,

**RAM,** `anup@almalinux-9-204:~$ free -h`

**CPU,** `anup@almalinux-9-204:~$ lscpu`

**Load,** `anup@almalinux-9-204:~$ top`

**Drive,** `anup@almalinux-9-204:~$ df -h`


### Change hostname,

`anup@almalinux-9-204:~$ sudo nano /etc/hostname`

`anup@almalinux-9-204:~$ sudo nano /etc/hosts`


### Configure static IP,

**Option 1: NMTUI**

`anup@almalinux-9-204:~$ sudo nmtui`


**Option 2: Manipulating Configuration File**

`anup@almalinux-9-204:~$ ls -ltr /etc/sysconfig/network-scripts/`

    # static IP address on CentOS 7 or RHEL 7#
    HWADDR=00:08:A2:0A:BA:B8
    TYPE=Ethernet
    BOOTPROTO=none
    
    # Server IP #
    IPADDR=192.168.2.203
    
    # Subnet #
    PREFIX=24
    
    # Set default gateway IP #
    GATEWAY=192.168.2.254
    
    # Set dns servers #
    DNS1=192.168.2.254
    DNS2=8.8.8.8
    DNS3=8.8.4.4
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    
    # Disable ipv6 #
    IPV6INIT=no
    NAME=eth0
    
    # This is system specific and can be created using 'uuidgen eth0' command #
    UUID=41171a6f-bce1-44de-8a6e-cf5e782f8bd6
    DEVICE=eth0
    ONBOOT=yes

`anup@almalinux-9-204:~$ nano /etc/sysconfig/network-scripts/ifcfg-eth0`

`anup@almalinux-9-204:~$ nano /etc/sysconfig/network-scripts/ifcfg-enp0s8`

    TYPE=Ethernet
    PROXY_METHOD=none
    BROWSER_ONLY=no
    BOOTPROTO=none
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=yes
    IPV6_AUTOCONF=yes
    IPV6_DEFROUTE=yes
    IPV6_FAILURE_FATAL=no
    IPV6_ADDR_GEN_MODE=stable-privacy
    NAME=enp0s8
    UUID=4badc384-161d-4a84-b898-a96deee91eef
    DEVICE=enp0s8
    ONBOOT=yes

    IPADDR=192.168.56.204
    PREFIX=24
    GATEWAY=92.168.56.1
    DNS1=8.8.8.8
    DNS2=8.8.4.4

`anup@almalinux-9-204:~$ ifconfig` **Find DEVICE and NAME**

`anup@almalinux-9-204:~$ blkid /dev/sda1` **Find UUID**

`anup@almalinux-9-204:~$ ls -lha /dev/disk/by-uuid` **Find UUID**

`anup@almalinux-9-204:~$ sudo systemctl restart NetworkManager.service`

`anup@almalinux-9-204:~$ sudo reboot now`


### Update,

`anup@almalinux-9-204:~$ cat /etc/os-release`

`anup@almalinux-9-204:~$ yum check-update`

`anup@almalinux-9-204:~$ yum update`

`anup@almalinux-9-204:~$ yum clean all`


### Configure firewall,

`anup@almalinux-9-204:~$ sudo systemctl status firewalld`

`anup@almalinux-9-204:~$ sudo systemctl start firewalld`

`anup@almalinux-9-204:~$ sudo systemctl enable firewalld`


`anup@almalinux-9-204:~$ sudo firewall-cmd --permanent --list-all`

`anup@almalinux-9-204:~$ sudo firewall-cmd --add-service=ssh --permanent`

`anup@almalinux-9-204:~$ sudo firewall-cmd --reload`

`anup@almalinux-9-204:~$ sudo firewall-cmd --permanent --add-service=http`

`anup@almalinux-9-204:~$ sudo firewall-cmd --permanent --add-service=https`

`anup@almalinux-9-204:~$ sudo firewall-cmd --permanent --add-service=smtp`

`anup@almalinux-9-204:~$ sudo firewall-cmd --permanent --list-all`


### Configure security-enhanced Linux (SELinux),

`anup@almalinux-9-204:~$ sestatus`

`anup@almalinux-9-204:~$ getenforce`

`anup@almalinux-9-204:~$ setenforce 0 (Permissive)`

`anup@almalinux-9-204:~$ setenforce 1 (Enforcing)`


### Users information,

`anup@almalinux-9-204:~$ less /etc/passwd`


### Create a new user,

`anup@almalinux-9-204:~$ sudo userdel anup`

`anup@almalinux-9-204:~$ sudo useradd anup`

`anup@almalinux-9-204:~$ passwd anup`

`anup@almalinux-9-204:~$ usermod -aG wheel anup`

`[root@almalinux-9-204 ~]# sudo su anup`


### Groups information,

`anup@almalinux-9-204:~$ less /etc/group`


### Monitor and remove unneeded services from it,

**Note :** Port, (2^16)-1, or 1-65535 are available, and ports in range 1-1023 are the privileged ones.

`anup@almalinux-9-204:~$ top`

`anup@almalinux-9-204:~$ sudo lsof -i -P -n | grep LISTEN`

`anup@almalinux-9-204:~$ sudo netstat -tulpn | grep LISTEN`


### Processes,

`anup@almalinux-9-204:~$ ps -aux`

`anup@almalinux-9-204:~$ top`


### Services / Daemons (d),

`anup@almalinux-9-204:~$ systemctl list-unit-files`

`anup@almalinux-9-204:~$ systemd-cgtop`


### Add public key authentication,

### Generate a key pair,

**On the local machine,**

`anup@almalinux-9-204:~$ pwd`

    /home/anup

`anup@almalinux-9-204:~$ ssh-keygen`

`anup@almalinux-9-204:~$ ls -ltra .ssh`


### Copy the public key,

### Option 1: Use ssh-copy-id

**On local machine**

`anup@almalinux-9-204:~$ ssh-copy-id users_name@server_ip`

`anup@almalinux-9-204:~$ ssh users_name@server_ip`


### Option 2: Manually install the key,

**On local machine**

`anup@almalinux-9-204:~$ cat ~/.ssh/id_rsa.pub (Copy the key to paste on the server)`


**On remote machine (Server),**

`anup@almalinux-9-204:~$ su users_name`

`anup@almalinux-9-204:~$ mkdir .ssh`

`anup@almalinux-9-204:~$ chmod 700 .ssh`

`anup@almalinux-9-204:~$ nano .ssh/authorized_keys (Paste the key from local)`

`anup@almalinux-9-204:~$ chmod 600 .ssh/authorized_keys`


**On local machine,**

`anup@almalinux-9-204:~$ ssh users_name@server_ip`


### Configure SSH daemon,

**On remote machine (Server),**

`anup@almalinux-9-204:~$ nano /etc/ssh/sshd_config`

    PermitRootLogin yes (Allow)

**or,**

    PermitRootLogin no (Do not allow)

`anup@almalinux-9-204:~$ systemctl reload sshd`

**On the local machine,**

`anup@almalinux-9-204:~$ ssh root@server_ip`


### List of repos,

`anup@almalinux-9-204:~$ ls /etc/yum.repos.d/`

`anup@almalinux-9-204:~$ sudo yum install epel-release`

`anup@almalinux-9-204:~$ yum repolist`


### Install basic system utilities,

`anup@almalinux-9-204:~$ yum install htop`

`anup@almalinux-9-204:~$ yum install multitail`


### Logs,

`anup@almalinux-9-204:~$ ls -ltr /var/log`


### Software details,

`anup@almalinux-9-204:~$ sudo yum list installed`

`anup@almalinux-9-204:~$ sudo yum list --installed | more`

`anup@almalinux-9-204:~$ sudo yum list --available`

`anup@almalinux-9-204:~$ sudo yum list --installed | wc -l`

`anup@almalinux-9-204:~$ sudo yum list --all | wc -l`

`anup@almalinux-9-204:~$ sudo yum list --available | wc -l`

`anup@almalinux-9-204:~$ sudo yum list --upgrades`

`anup@almalinux-9-204:~$ sudo yum list --upgrades | more`

`anup@almalinux-9-204:~$ sudo yum list --upgrades | grep -i kernel`


###  Installed packages with rpm command,

`anup@almalinux-9-204:~$ rpm -ivh httpd-2.0.46-32.ent.3.i386.rpm`

`anup@almalinux-9-204:~$ sudo rpm -qa`

`anup@almalinux-9-204:~$ sudo rpm -qa | more`

`anup@almalinux-9-204:~$ sudo rpm -qa | wc -l`

<br>
