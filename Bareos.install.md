## on Ubuntu installation
```
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


```

