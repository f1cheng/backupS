## backup
```


When at a prompt, entering a period cancels the command.

*run
Automatically selected Catalog: MyCatalog
Using Catalog "MyCatalog"
A job name must be specified.
The defined Job resources are:
     1: RestoreFiles
     2: backup-client2-fd
     3: BackupCatalog
     4: backup-bareos-fd
Select Job resource (1-4): 2

Select Job resource (1-4): 2
Run Backup job
JobName:  backup-client2-fd
Level:    Incremental
Client:   client2-fd
Format:   Native
FileSet:  windows10
Pool:     Incremental (From Job IncPool override)
Storage:  File (From Job resource)
When:     2019-05-19 00:22:22
Priority: 10
OK to run? (yes/mod/no): yes
Job queued. JobId=5

Job queued. JobId=5
*status
Status available for:
     1: Director
     2: Storage
     3: Client
     4: Scheduler
     5: All

Expected a positive integer, got: 
Select daemon type for status (1-5): 0
Please enter a number between 1 and 5
Select daemon type for status (1-5): All
Expected a positive integer, got: All
Select daemon type for status (1-5): 5
bareos-dir Version: 18.2.5 (30 January 2019) Linux-4.4.92-6.18-default ubuntu Ubuntu 16.04 LTS
Daemon started 19-5月019 00:14. Jobs: run=1, running=0 mode=0 db:mysql, bareos.org build binary
 Heap: heap=135,168 smbytes=170,048 max_bytes=190,032 bufs=526 max_bufs=776
No Scheduled Jobs.
====

Running Jobs:
Console connected at 19-5月019 00:20
No Jobs running.
====

Terminated Jobs:
 JobId  Level    Files      Bytes   Status   Finished        Name 
====================================================================
     1  Full        353    42.65 M  OK       11-5月019 21:01 BackupClient1
     2  Incr          0         0   OK       12-5月019 14:54 BackupClient1
     3              353    42.65 M  OK       12-5月019 15:07 RestoreFiles
     4  Full        353    42.65 M  OK       18-5月019 21:01 backup-bareos-fd
     5  Full          0         0   Error    19-5月019 00:23 backup-client2-fd


Client Initiated Connections (waiting for jobs):
Connect time        Protocol            Authenticated       Name                                    
====================================================================================================
====
Connecting to Storage daemon File at fred-Vostro-2420:9103

bareos-sd Version: 18.2.5 (30 January 2019) Linux-4.4.92-6.18-default ubuntu Ubuntu 16.04 LTS
Daemon started 18-5月019 17:05. Jobs: run=2, running=0, bareos.org build binary
 Heap: heap=110,592 smbytes=93,690 max_bytes=160,900 bufs=88 max_bufs=106
 Sizes: boffset_t=8 size_t=4 int32_t=4 int64_t=8 mode=0 bwlimit=0kB/s

Running Jobs:
No Jobs running.
====

Jobs waiting to reserve a drive:
====

Terminated Jobs:
 JobId  Level    Files      Bytes   Status   Finished        Name 
===================================================================
     1  Full        353    42.69 M  OK       11-5月019 21:01 BackupClient1
     2  Incr          0         0   OK       12-5月019 14:54 BackupClient1
     3                0         0   OK       12-5月019 15:07 RestoreFiles
     4  Full        353    42.69 M  OK       18-5月019 21:01 backup-bareos-fd
     5  Full          0         0   Cancel   19-5月019 00:23 backup-client2-fd
====

Device status:

Device "FileStorage" (/var/lib/bareos/storage) is not open.
==
====

Used Volume status:
====

====

Connecting to Client client2-fd at 192.168.0.8:9102
 Handshake: Immediate TLS, Encryption: PSK-AES256-CBC-SHA

client2-fd Version: 18.2.5 (30 January 2019)  VSS Linux Cross-compile Win64
Daemon started 19-May-19 00:17. Jobs: run=0 running=0, bareos.org build binary
Microsoft Windows 8 Enterprise Edition (build 9200), 64-bit
 Heap: heap=0 smbytes=57,254 max_bytes=61,432 bufs=71 max_bufs=114
 Sizeof: boffset_t=8 size_t=8 debug=0 trace=1 bwlimit=0kB/s

Running Jobs:
bareos-dir (director) connected at: 19-May-19 00:24
No Jobs running.
====

Terminated Jobs:
====
Connecting to Client bareos-fd at localhost:9102
Probing client protocol... (result will be saved until config reload)
 Handshake: Cleartext, Encryption: None

fred-Vostro-2420-fd Version: 18.2.5 (30 January 2019)  Linux-4.4.92-6.18-default ubuntu Ubuntu 16.04 LTS
Daemon started 18-5月019 17:05. Jobs: run=1 running=0, bareos.org build binary
 Heap: heap=0 smbytes=97,378 max_bytes=99,808 bufs=69 max_bufs=92
 Sizeof: boffset_t=8 size_t=4 debug=0 trace=0 bwlimit=0kB/s

Running Jobs:
bareos-dir (director) connected at: 19-5月019 00:24
No Jobs running.
====

Terminated Jobs:
 JobId  Level    Files      Bytes   Status   Finished        Name 
======================================================================
     1  Full        353    42.65 M  OK       11-5月019 21:01 BackupClient1
     2  Incr          0         0   OK       12-5月019 14:54 BackupClient1
     3              353    42.65 M  OK       12-5月019 15:07 RestoreFiles
     4  Full        353    42.65 M  OK       18-5月019 21:01 backup-bareos-fd
====


```
