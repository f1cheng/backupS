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

```

