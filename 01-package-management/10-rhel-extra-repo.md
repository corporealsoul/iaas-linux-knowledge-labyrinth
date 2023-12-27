
### Install EPEL in 2 easy steps On RHEL,

https://www.redhat.com/sysadmin/install-epel-linux


**Let's check,**

    [anup@rhel-92-04 ~]$ sudo dnf install inxi


**First, enable the CodeReady Linux Builder repository. You already have access to it; you just need to enable it,**

    [anup@rhel-92-04 ~]$ sudo subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms


**Next, install the EPEL RPM,**

    [anup@rhel-92-04 ~]$ sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm


**Check again,**

    [anup@rhel-92-04 ~]$ sudo dnf install inxi


**Check by,**

    [anup@rhel-92-04 ~]$ yum repolist
    
    [anup@rhel-92-04 ~]$ yum repolist enabled 

<br>
