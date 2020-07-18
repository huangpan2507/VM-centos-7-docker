# VM-centos-7-docker
vm虚拟机 设置网络，NAT模式时 static IP时，按各种博客出现无法上网问题



解决如下：
https://blog.csdn.net/chinabate/article/details/84900286


1.window下 ipconfig 

找到默认网关：我的为192.168.1.1

2. linux下 ipconfig
ens33 inet：192.168.1.71  netmask 255.255.255.0


3. /etc/sysconfig/network-scripts/ifcfg-ens33  文件如下：
TYPE=Ethernet
BOOTPROTO=none
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33
UUID=d823e897-9310-4aa4-bc42-e5f25b7a5926
DEVICE=ens33
ONBOOT=yes
DNS1=8.8.8.8
IPADDR=192.168.1.71
PREFIX=24
GATEWAY=192.168.1.1
IPV6_PEERDNS=yes
IPV6_PEERROUTES=yes

4.service network restart

