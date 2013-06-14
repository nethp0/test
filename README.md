test
====

xx.txt.com

#!/bin/sh

sdb="""NetworkManager
avahi-daemon
bluetooth
cups
cimserver
firstboot
gpm
hidd
hpiod
ip6tables
kudzu
netfs
nfs
nfslock
pcscd
portmap
rpcgssd
rpcidmapd
sendmail
xfs
xinetd
Xorg
exim
yum-updatesd""" 
for i in $sdb
do 
#       for n in `chkconfig --list | grep 3:on |awk '{print $1}'`
        for n in `ls /etc/init.d`
        do
        if [ $i == $n ];then
        /etc/init.d/$n stop
        chkconfig --level 35 $n off
        fi
        done

done
