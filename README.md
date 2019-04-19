# Installation Guide

## Currently, Linux Kernel 4.9 and above have integrated BBR, so you only need to upgrade Kernel.

## CentOS Linux 6 installation:

## Enter your CentOS, first upgrade your CentOS Linux 6 to the latest version (currently the latest version is 6.9):
```yum -y update```

## Please use the following command to view the version number of CentOS Linux:
```cat /etc/redhat-release```
##### CentOS release 6.9 (Final)

## then use yum to install wget (if you have installed, you can ignore this step):
```yum -y install wget```

## Ricky personally likes to put some temporary files in the /tmp directory, so enter the /tmp directory, use the wget command to download the installation script here, and execute the script:
```cd /tmp && wget --no-check-certificate https://raw.githubusercontent.com/jm051484/centos6/master/BBR.sh && rm -f BBR.sh && sh BBR.sh```

## CentOS Linux 6 BBR installation script content please refer to the end of this article.

## After the CentOS Linux 6 restarts, use the following command to check whether the BBR is enabled:

```cat /etc/redhat-release```
##### CentOS release 6.9 (Final)

```uname -r```
##### 4.14.11-1.el6.elrepo.x86_64

```lsmod | grep bbr```
##### tcp_bbr                16384  26 

```echo "net.core.default_qdisc = fq" >> /etc/sysctl.conf && echo "net.ipv4.tcp_congestion_control = bbr" >> /etc/sysctl.conf && sysctl --system && sysctl net.ipv4.tcp_available_congestion_control```
##### net.ipv4.tcp_available_congestion_control = bbr cubic reno

## At this point, the installation is complete.
