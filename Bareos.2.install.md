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

```
