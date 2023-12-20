### SSH to the server,

`anup@ubunut-20046:~$ sudo apt-get install net-tools`

`anup@ubunut-20046:~$ sudo apt-get install openssh-server`

`anup@ubunut-20046:~$ sudo apt-get install openssh-client`


`anup@ubunut-20046:~$ ifconfig`

`PS C:\Users\uniqs> ssh anup@192.168.56.101`

<br>

### Platform,

`anup@ubunut-20046:~$ cat /etc/os-release`

`anup@ubunut-20046:~$ hostnamectl`

`anup@ubunut-20046:~$ lsb_release -a`

<br>

### Change hostname,

`anup@ubunut-20046:~$ sudo nano /etc/hostname`

    ubunut-20046

`anup@ubunut-20046:~$ sudo nano /etc/hosts`

    127.0.0.1 localhost
    127.0.1.1 ubunut-20046
    
    # The following lines are desirable for IPv6 capable hosts
    ::1     ip6-localhost ip6-loopback
    fe00::0 ip6-localnet
    ff00::0 ip6-mcastprefix
    ff02::1 ip6-allnodes
    ff02::2 ip6-allrouters

`anup@ubunut-20046:~$ hostnamectl`

`anup@ubunut-20046:~$ getent hosts`

<br>

### Configure static IP,

`anup@ubunut-20046:~$ sudo nano /etc/cloud/cloud.cfg.d/subiquity-disable-cloudinit-networking.cfg`

    network: {config: disabled}


`anup@ubunut-20046:~$ sudo cp /etc/netplan/00-installer-config.yaml /etc/netplan/00-installer-config.yaml.backup`

`anup@ubunut-20046:~$ sudo nano /etc/netplan/00-installer-config.yaml`

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

`anup@ubunut-20046:~$ sudo netplan try`

`anup@ubunut-20046:~$ sudo netplan apply`

<br>

### Update,

`anup@ubunut-20046:~$ sudo apt-get update`

`anup@ubunut-20046:~$ sudo apt-get upgrade`

<br>

### System Information,

`anup@ubunut-20046:~$ uname -a`

<br>

### Users information,

`anup@ubunut-20046:~$ less /etc/passwd`

<br>

### Creating a New User,

`anup@ubunut-20046:~$ adduser ubuntu-user`

`anup@ubunut-20046:~$ usermod -aG sudo ubuntu-user`

`anup@ubunut-20046:~$ finger ubuntu-user`

<br>

### Groups information,

`anup@ubunut-20046:~$ less /etc/group`

<br>

### Resources,

**RAM,** `anup@ubunut-20046:~$ free -h`

**CPU,** `anup@ubunut-20046:~$ lscpu`

**Load,** `anup@ubunut-20046:~$ htop`

**Drive,** `anup@ubunut-20046:~$ df -h`

<br>

### Processes,

`anup@ubunut-20046:~$ ps -aux`

`anup@ubunut-20046:~$ htop`

<br>

### Services / Daemons (d),

`anup@ubunut-20046:~$ systemctl list-unit-files`

`anup@ubunut-20046:~$ systemd-cgtop`

`anup@ubunut-20046:~$ ps -eo 'tty,pid,comm' | grep ^?` , Processes per Services / Daemons

<br>

### Ports,

**Note :** Port, (2^16)-1, or 1-65535 are available, and ports in range 1-1023 are the privileged ones.

`anup@ubunut-20046:~$ sudo lsof -i -P -n | grep LISTEN`

`anup@ubunut-20046:~$ sudo netstat -tulpn | grep LISTEN`

<br>

### Firewall,

`anup@ubunut-20046:~$ sudo ufw status`

`anup@ubunut-20046:~$ sudo ufw enable`

`anup@ubunut-20046:~$ sudo ufw allow OpenSSH`

`anup@ubunut-20046:~$ sudo ufw allow 22`

`anup@ubunut-20046:~$ sudo ufw app list`

`anup@ubunut-20046:~$ sudo ufw status`

<br>

### Install basic system utilities,

`anup@ubunut-20046:~$ sudo apt-get install software-properties-common`

`anup@ubunut-20046:~$ sudo apt-get install htop`

`anup@ubunut-20046:~$ sudo apt-get install multitail`

<br>

### Logs,

`anup@ubunut-20046:~$ ls -ltr /var/log`

<br>

### List of repos,

`anup@ubunut-20046:~$ cat /etc/apt/sources.list`

<br>

### Software details,

`anup@ubunut-20046:~$ apt list`

`anup@ubunut-20046:~$ apt list --installed`

`anup@ubunut-20046:~$ apt list --upgradeable`

`anup@ubunut-20046:~$ apt list apache2`

`anup@ubunut-20046:~$ apt list | grep nginx`

<br>

`anup@ubunut-20046:~$ dpkg --list`

`anup@ubunut-20046:~$ dpkg --list | grep nginx`

<br>
