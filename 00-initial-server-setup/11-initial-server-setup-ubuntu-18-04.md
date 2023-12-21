### SSH to the server,

`anup@ubuntu-18046:~$ sudo apt-get install net-tools`

`anup@ubuntu-18046:~$ sudo apt-get install openssh-server`

`anup@ubuntu-18046:~$ sudo apt-get install openssh-client`


`anup@ubuntu-18046:~$ ifconfig`

`PS C:\Users\uniqs> ssh anup@192.168.56.101`

<br>

### Platform,

`anup@ubuntu-18046:~$ cat /etc/os-release`

`anup@ubuntu-18046:~$ hostnamectl`

`anup@ubuntu-18046:~$ lsb_release -a`

<br>

### Change hostname,

`anup@ubuntu-18046:~$ sudo nano /etc/hostname`

    ubuntu-18046

`anup@ubuntu-18046:~$ sudo nano /etc/hosts`

    127.0.0.1 localhost
    127.0.1.1 ubuntu-18046
    
    # The following lines are desirable for IPv6 capable hosts
    ::1     ip6-localhost ip6-loopback
    fe00::0 ip6-localnet
    ff00::0 ip6-mcastprefix
    ff02::1 ip6-allnodes
    ff02::2 ip6-allrouters

`anup@ubuntu-18046:~$ hostnamectl`

`anup@ubuntu-18046:~$ getent hosts`

<br>

### Configure static IP,

`anup@ubuntu-18046:~$ sudo nano /etc/cloud/cloud.cfg.d/subiquity-disable-cloudinit-networking.cfg`

    network: {config: disabled}


`anup@ubuntu-18046:~$ sudo cp /etc/netplan/00-installer-config.yaml /etc/netplan/00-installer-config.yaml.backup`

`anup@ubuntu-18046:~$ sudo nano /etc/netplan/00-installer-config.yaml`

    # This is the network config written by 'subiquity'
    network:
      version: 2
      renderer: networkd
      ethernets:
        enp0s3:
          dhcp4: yes
        enp0s8:
          addresses: [192.168.56.10/24]
          dhcp4: false

`anup@ubuntu-18046:~$ sudo netplan try`

`anup@ubuntu-18046:~$ sudo netplan apply`

<br>

### Update,

`anup@ubuntu-18046:~$ sudo apt-get update`

`anup@ubuntu-18046:~$ sudo apt-get upgrade`

<br>

### System Information,

`anup@ubuntu-18046:~$ uname -a`

<br>

### Users information,

`anup@ubuntu-18046:~$ less /etc/passwd`

<br>

### Creating a New User,

`anup@ubuntu-18046:~$ adduser ubuntu-user`

`anup@ubuntu-18046:~$ usermod -aG sudo ubuntu-user`

`anup@ubuntu-18046:~$ finger ubuntu-user`

<br>

### Groups information,

`anup@ubuntu-18046:~$ less /etc/group`

<br>

### Resources,

**RAM,** `anup@ubuntu-18046:~$ free -h`

**CPU,** `anup@ubuntu-18046:~$ lscpu`

**Load,** `anup@ubuntu-18046:~$ htop`

**Drive,** `anup@ubuntu-18046:~$ df -h`

<br>

### Processes,

`anup@ubuntu-18046:~$ ps -aux`

`anup@ubuntu-18046:~$ htop`

<br>

### Services / Daemons (d),

`anup@ubuntu-18046:~$ systemctl list-unit-files`

`anup@ubuntu-18046:~$ systemd-cgtop`

`anup@ubuntu-18046:~$ ps -eo 'tty,pid,comm' | grep ^?` , Processes per Services / Daemons

<br>

### Ports,

**Note :** Port, (2^16)-1, or 1-65535 are available, and ports in range 1-1023 are the privileged ones.

`anup@ubuntu-18046:~$ sudo lsof -i -P -n | grep LISTEN`

`anup@ubuntu-18046:~$ sudo netstat -tulpn | grep LISTEN`

<br>

### Firewall,

`anup@ubuntu-18046:~$ sudo ufw status`

`anup@ubuntu-18046:~$ sudo ufw enable`

`anup@ubuntu-18046:~$ sudo ufw allow OpenSSH`

`anup@ubuntu-18046:~$ sudo ufw allow 22`

`anup@ubuntu-18046:~$ sudo ufw app list`

`anup@ubuntu-18046:~$ sudo ufw status`

<br>

### Install basic system utilities,

`anup@ubuntu-18046:~$ sudo apt-get install software-properties-common`

`anup@ubuntu-18046:~$ sudo apt-get install htop`

`anup@ubuntu-18046:~$ sudo apt-get install multitail`

<br>

### Logs,

`anup@ubuntu-18046:~$ ls -ltr /var/log`

<br>

### List of repos,

`anup@ubuntu-18046:~$ cat /etc/apt/sources.list`

<br>

### Software details,

`anup@ubuntu-18046:~$ apt list`

`anup@ubuntu-18046:~$ apt list --installed`

`anup@ubuntu-18046:~$ apt list --upgradeable`

`anup@ubuntu-18046:~$ apt list apache2`

`anup@ubuntu-18046:~$ apt list | grep nginx`

<br>

`anup@ubuntu-18046:~$ dpkg --list`

`anup@ubuntu-18046:~$ dpkg --list | grep nginx`

<br>
