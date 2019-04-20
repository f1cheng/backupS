```
root@fred-Vostro-2420:~# mkdir -p /var/data/amanda/vtape/DailySet2
root@fred-Vostro-2420:~# chown -R backup:disk /var/data/amanda/vtape/DailySet2
root@fred-Vostro-2420:~# chmod -R 750 /var/data/amanda/vtape/DailySet2
root@fred-Vostro-2420:~# 

backup@fred-Vostro-2420:~$ amserverconfig DailySet2 --template harddisk  --tapedev /var/data/amanda/vtape/DailySet2 --mailto 184918308@qq.com --dumpcycle 1week --runspercycle 5 --tapecycle 12 --runtapes 1
Logging to /var/log/amanda/amserverconfig.20190420163102.debug
mkdir /etc/amanda/DailySet2
/var/lib/amanda/gnutar-lists directory exists
/etc/amanda/DailySet2/advanced.conf created and updated
mkdir /etc/amanda/DailySet2/curinfo
mkdir /etc/amanda/DailySet2/index
curinfo and index directory created
tapelist file created
disklist file created
Creating custom configuration using templates
custom amanda.conf created
creating vtape directory
amlabel vtapes
mkdir slot1
mkdir slot11
mkdir slot12
changer is reset
/usr/share/doc/amanda-server/examples/xinetd.amandaserver contains the latest Amanda server daemon configuration.
Please merge it to /etc/xinetd.d/amandaserver.
DONE.
!!!not amandaserver, it's /etc/xinetd.d/amanda


!!it needs password input for backup user.
backup@fred-Vostro-2420:~$ amaddclient --config DailySet2 --client c.amanda.com --diskdev /home/fred/downloads --dumptype comp-user-tar
Logging to /var/log/amanda/amaddclient.20190420163719.debug
/etc/amanda/DailySet2/disklist updated
updating /var/lib/lib/amanda/.amandahosts on fred-Vostro-2420
/var/lib/lib/amanda/.amandahosts contains c.amanda.com root, file not updated
Attempting to update /var/lib/lib/amanda/.amandahosts on c.amanda.com
The authenticity of host 'c.amanda.com (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:eQcK6dIjC74oY7rB+wx7aQYEjQprP5xHw62S40tmmNY.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'c.amanda.com' (ECDSA) to the list of known hosts.
backup@c.amanda.com's password: 
.amandahosts                                                                                                 100%  111     0.1KB/s   00:00    
/var/lib/lib/amanda/.amandahosts contains fred-Vostro-2420 backup, file not updated
c.amanda.com:/var/lib/lib/amanda/.amandahosts updated successfully
Creating amanda-client.conf for c.amanda.com
Creating  /etc/amanda/DailySet2 on c.amanda.com
backup@c.amanda.com's password: 
backup@c.amanda.com's password: 
amanda-client.conf-c.amanda.com                                                                              100%  388     0.4KB/s   00:00    
Copy /var/lib/lib/amanda/amanda-client.conf-c.amanda.com to c.amanda.com successfully
File /var/lib/amanda/example/xinetd.amandaclient contains the latest Amanda client daemon configuration.
Please merge it to /etc/xinetd.d/amandaclient.
!! not not amandaclient, rather amanda

backup@fred-Vostro-2420:~$ amcheck -c DailySet2

Amanda Backup Client Hosts Check
--------------------------------
Client check: 1 host checked in 1.231 seconds.  0 problems found.

(brought to you by Amanda 3.3.6)
backup@fred-Vostro-2420:~$ 

backup@fred-Vostro-2420:~$ amdump DailySet2
backup@fred-Vostro-2420:~$ 
backup@fred-Vostro-2420:~$ 


backup@fred-Vostro-2420:~$ amadmin DailySet2 find c.amanda /home

date                host         disk                 lv tape or file file part status
2019-04-20 16:44:52 c.amanda.com /home/fred/downloads  0 DailySet2-1     1  1/1 OK 
backup@fred-Vostro-2420:~$ 


backup@fred-Vostro-2420:/var/data/amanda/vtape/DailySet2/data$ ls -lrt
总用量 1152
-rw------- 1 backup backup   32768 4月  20 16:44 00000.DailySet2-1
-rw------- 1 backup backup 1146848 4月  20 16:44 00001.c.amanda.com._home_fred_downloads.0
backup@fred-Vostro-2420:/var/data/amanda/vtape/DailySet2/data$ 


backup@fred-Vostro-2420:/var/data/amanda/vtape/DailySet2/data$ mkdir /tmp/restore/
backup@fred-Vostro-2420:/var/data/amanda/vtape/DailySet2/data$ cd /tmp/restore/
backup@fred-Vostro-2420:/tmp/restore$ ls
backup@fred-Vostro-2420:/tmp/restore$ amfetchdump DailySet2 c.amanda.com /home/fred/
1 volume(s) needed for restoration
The following volumes are needed: DailySet2-1
Press enter when ready


amfetchdump: 1: restoring split dumpfile: date 20190420164452 host c.amanda.com disk /home/fred/downloads part 1/UNKNOWN lev 0 comp .gz program /bin/tar

1087 kb 
backup@fred-Vostro-2420:/tmp/restore$ ls
c.amanda.com._home_fred_downloads.20190420164452.0
backup@fred-Vostro-2420:/tmp/restore$ 


backup@fred-Vostro-2420:/tmp/restore$ tar -xvf c.amanda.com._home_fred_downloads.20190420164452.0
./
./jj.txt
./libzmq-master.zip
backup@fred-Vostro-2420:/tmp/restore$ ls -lrt
总用量 2492
-rw-rw-r-- 1 backup backup 1268546 1月  21  2018 libzmq-master.zip
-rw-rw-r-- 1 backup backup       0 4月  20 16:36 jj.txt
-rw------- 1 backup backup 1280000 4月  20 16:48 c.amanda.com._home_fred_downloads.20190420164452.0
backup@fred-Vostro-2420:/tmp/restore$ 
```
