# Installation Guide

Currently, Linux Kernel 4.9 and above have integrated BBR, so you only need to upgrade Kernel.

CentOS Linux 6 installation:
1. Enter your CentOS, first upgrade your CentOS Linux 6 to the latest version (currently the latest version is 6.9):

[root@host ~]# yum -y update
Please use the following command to view the version number of CentOS Linux:

[root@host ~]# cat /etc/redhat-release
CentOS release 6.9 (Final)
2, then use yum to install wget (if you have installed, you can ignore this step):

[root@host ~]# yum -y install wget
3. Ricky personally likes to put some temporary files in the /tmp directory, so enter the /tmp directory, use the wget command to download the installation script here, and execute the script:

[root@host ~]# cd /tmp && wget --no-check-certificate https://raw.githubusercontent.com/jm051484/centos6/master/BBR.sh && rm -f BBR.sh && sh BBR.sh

CentOS Linux 6 BBR installation script content please refer to the end of this article.

4. After the CentOS Linux 6 restarts, use the following command to check whether the BBR is enabled:

[root@host ~]# cat /etc/redhat-release 
CentOS release 6.9 (Final)

[root@host ~]# uname -r
4.14.11-1.el6.elrepo.x86_64

[root@host ~]# lsmod | grep bbr
tcp_bbr                16384  26 

[root@host ~]# echo "net.core.default_qdisc = fq" >> /etc/sysctl.conf && echo "net.ipv4.tcp_congestion_control = bbr" >> /etc/sysctl.conf && sysctl --system && sysctl net.ipv4.tcp_available_congestion_control
net.ipv4.tcp_available_congestion_control = bbr cubic reno

At this point, the installation is complete.
