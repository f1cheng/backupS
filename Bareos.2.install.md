## abc

```

root@fred-Vostro-2420:/etc/bareos# vi ./bareos-dir.d/director/bareos-dir.conf
root@fred-Vostro-2420:/etc/bareos# service bareos-dir restart
root@fred-Vostro-2420:/etc/bareos# lsb_release
No LSB modules are available.
您在 /var/mail/root 中有新邮件
root@fred-Vostro-2420:/etc/bareos# lsb_release -sr
16.04
root@fred-Vostro-2420:/etc/bareos# RELEASE=release/latest
root@fred-Vostro-2420:/etc/bareos# DIST=xUbuntu_$(lsb_release -sr)
root@fred-Vostro-2420:/etc/bareos# echo $DIST
xUbuntu_16.04
root@fred-Vostro-2420:/etc/bareos# URL=http://download.bareos.org/bareos/$RELEASE/$DIST
root@fred-Vostro-2420:/etc/bareos# echo $URL
http://download.bareos.org/bareos/release/latest/xUbuntu_16.04
root@fred-Vostro-2420:/etc/bareos# printf "deb $URL /\n" tee /etc/apt/sources.list.d/bareos.list
deb http://download.bareos.org/bareos/release/latest/xUbuntu_16.04 /
root@fred-Vostro-2420:/etc/bareos# more /etc/apt/sources.list.d/bareos.list 
deb http://download.bareos.org/bareos/release/17.2/xUbuntu_16.04 /
root@fred-Vostro-2420:/etc/bareos# wget -q $URL/Release.key -O- | apt-key add -
OK

root@fred-Vostro-2420:/etc/bareos# vi /etc/apt/sources.list.d/bareos.list root@fred-Vostro-2420:/etc/bareos# printf "deb $URL /\n" > /etc/apt/sources.list.d/bareos.list
root@fred-Vostro-2420:/etc/bareos# vi /etc/apt/sources.list.d/bareos.list root@fred-Vostro-2420:/etc/bareos# vi /etc/apt/sources.list.d/bareos.list 
root@fred-Vostro-2420:/etc/bareos# wget -q $URL/Release.key -O- | apt-key add -OK
root@fred-Vostro-2420:/etc/bareos# apt install mariadb-server bareos bareos-database-mysql
正在读取软件包列表... 完成

正在安装新版本配置文件 /etc/bareos-webui/directors.ini ...
正在安装新版本配置文件 /etc/bareos/bareos-dir.d/console/admin.conf.example ...
/usr/sbin/a2enmod
Module rewrite already enabled
/usr/sbin/a2enmod
Module rewrite already enabled
/usr/sbin/a2enconf
Conf bareos-webui already enabled
您在 /var/mail/root 中有新邮件
root@fred-Vostro-2420:/etc/bareos# 



root@fred-Vostro-2420://usr/share/bareos-webui# vi /usr/share/bareos-webui/vendor/Bareos/library/Bareos/BSock/BareosBSock.php
root@fred-Vostro-2420://usr/share/bareos-webui# service apache2 restart
root@fred-Vostro-2420://usr/share/bareos-webui# vi /usr/share/bareos-webui/vendor/Bareos/library/Bareos/BSock/BareosBSock.php
root@fred-Vostro-2420://usr/share/bareos-webui# cd


root@fred-Vostro-2420:/etc/bareos# bconsole
Connecting to Director fred-Vostro-2420:9101
 Encryption: None
1000 OK: fred-Vostro-2420-dir Version: 18.2.5 (30 January 2019)
bareos.org build binary
bareos.org binaries are UNSUPPORTED by bareos.com.
Get official binaries and vendor support on https://www.bareos.com
You are connected using the default console

Enter a period to cancel a command.
*configure add console name=admin password=admin profile=webui-admin
It seems that the configuration is not adapted to the include directory structure. This means, that the configure command may not work as expected. Your configuration changes may not survive a reload/restart. Resource config file "/etc/bareos/bareos-dir.d/console/admin.conf" already exists.
You have messages.
*

log info:
^C
root@fred-Vostro-2420:/var/log/bareos# ls -lrt
总用量 16
-rw-r----- 1 bareos bareos  766 5月  11 15:47 bareos-audit.log
-rw-r--r-- 1 bareos bareos 8409 5月  11 21:01 bareos.log
root@fred-Vostro-2420:/var/log/bareos# 






```
