
=============configuraitons
``` 
==Amanda service(client and server) config:amanda

root@fred-Vostro-2420:~# more /etc/xinetd.d/amanda 
# default: on
#
# description: Amanda services for Amanda server and client.
#

service amanda
{
        disable         = no
        flags           = IPv4
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = backup
        group           = disk
        groups          = yes
        server          = /usr/lib/amanda/amandad
        server_args     = -auth=bsdtcp amdump amindexd amidxtaped
}
root@fred-Vostro-2420:~# 

==Amanda peer hosts: .amandahosts(manually)

root@fred-Vostro-2420:/etc/xinetd.d# more /var/lib/lib/amanda/.amandahosts 
c.amanda.com  root amindexd amidxtaped
s.amanda.com  root amindexd amidxtaped

fred-Vostro-2420  backup amdump
root@fred-Vostro-2420:/etc/xinetd.d# 

---
root@fred-Vostro-2420:/etc/xinetd.d# ls -lart /var/lib/lib/amanda/
总用量 12
drwxr-xr-x 3 root   root   4096 4月  15 21:27 ..
-rw------- 1 backup backup  111 4月  15 21:34 .amandahosts
drwxr-xr-x 2 backup disk   4096 4月  15 21:35 .
root@fred-Vostro-2420:/etc/xinetd.d# cd /var/lib/lib
root@fred-Vostro-2420:/var/lib/lib# ls -lrart
总用量 12
drwxr-xr-x 96 root   root 4096 4月  15 21:27 ..
drwxr-xr-x  3 root   root 4096 4月  15 21:27 .
drwxr-xr-x  2 backup disk 4096 4月  15 21:35 amanda

==Amanda server config(amserverconfig)
/etc/amanda/DailySet1/amanda.conf
root@fred-Vostro-2420:/var# more /etc/amanda/DailySet1/amanda.conf
org "DailySet1"		# your organization name for reports
dumpuser "backup"	# the user to run dumps under
mailto "184918308@qq.com"	# space separated list of operators at your site
dumpcycle 1week		# the number of days in the normal dump cycle
runspercycle 5		# the number of amdump runs in dumpcycle days
tapecycle 12	# the number of tapes in rotation
runtapes 1		# number of tapes to be used in a single run of amdump

define changer my_vtapes {
    tpchanger "chg-disk:/var/data/amanda/vtape/DailySet1"
    property "num-slot" "10"
    property "auto-create-slot" "yes"
}
tpchanger "my_vtapes"

tapetype HARDDISK	# what kind of tape it is
labelstr "DailySet1"	# label constraint regex: all tapes must match
dtimeout 1800	# number of idle seconds before a dump is aborted
ctimeout 30	# max number of secconds amcheck waits for each client
etimeout 300	# number of seconds per filesystem for estimates
define dumptype global {
       comment "Global definitions"
       auth "bsdtcp"
}
define dumptype gui-base {
       global
       program "GNUTAR"
       comment "gui base dumptype dumped with tar"
       compress none
       index yes
}
define tapetype HARDDISK {
       comment "Virtual Tapes"
       length 5000 mbytes
}
includefile "advanced.conf"
includefile "/etc/amanda/template.d/dumptypes"
includefile "/etc/amanda/template.d/tapetypes"
```  
