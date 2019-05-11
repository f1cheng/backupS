## on Ubuntu installation
```

RELEASE=release/17.2/
#Bareos

2019年 05月 11日 星期六 15:17:08 CST
root@fred-Vostro-2420:~# /usr/lib/bareos/scripts/create_bareos_database 
Creating postgresql database
Unable to determine PostgreSQL version.
root@fred-Vostro-2420:~# cd /usr/lib/bareos/scripts/
root@fred-Vostro-2420:/usr/lib/bareos/scripts# vi create_bareos_database 
root@fred-Vostro-2420:/usr/lib/bareos/scripts# ./create_bareos_database mysql
Creating mysql database
Creating of bareos database succeeded.
root@fred-Vostro-2420:/usr/lib/bareos/scripts# ./make_bareos_tables mysql
Making mysql tables
Creation of Bareos MySQL tables succeeded.
root@fred-Vostro-2420:/usr/lib/bareos/scripts# ./grant_bareos_privileges mysql
Granting mysql tables
Privileges for user bareos granted ON database bareos.
root@fred-Vostro-2420:/usr/lib/bareos/scripts# service bareos-dir start
root@fred-Vostro-2420:/usr/lib/bareos/scripts# service bareos-dir status
● bareos-director.service - Bareos Director Daemon service
   Loaded: loaded (/lib/systemd/system/bareos-director.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since 六 2019-05-11 15:22:01 CST; 54s ago
     Docs: man:bareos-dir(8)
  Process: 9869 ExecStart=/usr/sbin/bareos-dir (code=exited, status=0/SUCCESS)
  Process: 9857 ExecStartPre=/usr/sbin/bareos-dir -t -f (code=exited, status=1/FAILURE)
 Main PID: 9872 (code=exited, status=1/FAILURE)

5月 11 15:21:01 fred-Vostro-2420 systemd[1]: Starting Bareos Director Daemon service...
5月 11 15:21:31 fred-Vostro-2420 bareos-dir[9857]: bareos-dir: dird.c:1161-0 Could not open Catalog "MyCatalog", database "bareos".
5月 11 15:21:31 fred-Vostro-2420 systemd[1]: bareos-director.service: PID file /var/lib/bareos/bareos-dir.9101.pid not readable (yet?) after st
5月 11 15:21:31 fred-Vostro-2420 systemd[1]: Started Bareos Director Daemon service.

root@fred-Vostro-2420:/etc/bareos# ls
bareos-dir.conf  bareos-dir-export  bareos-fd.d     bareos-sd.d    bconsole.conf.dist  tray-monitor.d
bareos-dir.d     bareos-fd.conf     bareos-sd.conf  bconsole.conf  tray-monitor.conf
root@fred-Vostro-2420:/etc/bareos# cd bareos-dir.d/console/
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# ls
admin.conf.example  bareos-mon.conf
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# cp admin.conf.example admin.conf
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# vi admin.conf
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# bconsole
Connecting to Director fred-Vostro-2420:9101
1000 OK: fred-Vostro-2420-dir Version: 17.2.4 (21 Sep 2017)
Enter a period to cancel a command.
*configure add console name=admin password=admin profile=webui-admin
It seems that the configuration is not adapted to the include directory structure. This means, that the configure command may not work as expected. Your configuration changes may not survive a reload/restart. Please see http://doc.bareos.org/master/html/bareos-manual-main-reference.html#ConfigurationIncludeDirectory for details.
Resource config file "/etc/bareos/bareos-dir.d/console/admin.conf" already exists.
*

root@fred-Vostro-2420:/etc/apache2# more ports.conf 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80

<IfModule ssl_module>
	Listen 443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
root@fred-Vostro-2420:/etc/apache2# 
root@fred-Vostro-2420:/etc/apache2# sed -i s/80/81/g ports.conf
root@fred-Vostro-2420:/etc/apache2# sed -i s/443/8443/g ports.conf
root@fred-Vostro-2420:/etc/apache2# more ports.conf 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 81

<IfModule ssl_module>
	Listen 8443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 8443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
root@fred-Vostro-2420:/etc/apache2# a2dissite 000-default
Site 000-default disabled.
To activate the new configuration, you need to run:
  service apache2 reload
root@fred-Vostro-2420:/etc/apache2# service appach2 reload
appach2: unrecognized service
root@fred-Vostro-2420:/etc/apache2# service appache2 reload
appache2: unrecognized service
root@fred-Vostro-2420:/etc/apache2# service apache2 reload
apache2.service is not active, cannot reload.
root@fred-Vostro-2420:/etc/apache2# service apache2 restart

root@fred-Vostro-2420:/etc/bareos# mysql --user=bareos --password=charging bareos
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 68
Server version: 10.0.38-MariaDB-0ubuntu0.16.04.1 Ubuntu 16.04

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [bareos]> 
MariaDB [bareos]> show tables;
+--------------------+
| Tables_in_bareos   |
+--------------------+
| BaseFiles          |
| Client             |
| Counters           |

show databases;


```

