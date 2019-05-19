
## win10 issue
```

*estimate job=backup-client2-fd listing client=client2-fd fileset=windows10
Using Catalog "MyCatalog"
Connecting to Client client2-fd at 192.168.0.8:9102
-rwxrwxrwx   1 0        0                  5 2019-05-01 11:32:18  c:/T/CFN/my1.txt
drwxrwxrwx   0 0        0                  0 2019-05-01 11:32:15  c:/T/CFN
-rwxrwxrwx   1 0        0                 27 2019-05-18 23:37:19  c:/T/j.txt
-rwxrwxrwx   1 0        0                  5 2019-05-19 00:59:41  c:/T/jj.t.tt
drwxrwxrwx   0 0        0                  0 2019-05-19 00:59:41  c:/T
2000 OK estimate files=5 bytes=37
*
==
*estimate job=backup-client2-fd listing client=client2-fd fileset=windows10
Using Catalog "MyCatalog"
Connecting to Client client2-fd at 192.168.0.8:9102
-rwxrwxrwx   1 0        0                  6 2019-05-19 14:52:38  c:/T/14dian.txt
-rwxrwxrwx   1 0        0                  5 2019-05-01 11:32:18  c:/T/CFN/my1.txt
drwxrwxrwx   0 0        0                  0 2019-05-01 11:32:15  c:/T/CFN
-rwxrwxrwx   1 0        0                 27 2019-05-18 23:37:19  c:/T/j.txt
-rwxrwxrwx   1 0        0                  5 2019-05-19 00:59:41  c:/T/jj.t.tt
drwxrwxrwx   0 0        0                  0 2019-05-19 14:52:35  c:/T
2000 OK estimate files=6 bytes=43
*


```

```
root@fred-Vostro-2420:/var/lib/bareos/storage# vi /var/mail/root 
您在 /var/mail/root 中有新邮件



19-5月 11:46 bareos-dir JobId 11: No prior Full backup Job record found.
19-5月 11:46 bareos-dir JobId 11: No prior or suitable Full backup found in catalog. Doing FULL backup.
19-5月 11:46 bareos-dir JobId 11: Start Backup JobId 11, Job=backup-client2-fd.2019-05-19_11.46.06_04
19-5月 11:46 bareos-dir JobId 11: Connected Storage daemon at fred-Vostro-2420:9103, encryption: PSK-AES256-CBC-SHA
19-5月 11:46 bareos-dir JobId 11: Using Device "FileStorage" to write.
19-5月 11:46 bareos-dir JobId 11: Probing client protocol... (result will be saved until config reload)
19-5月 11:46 bareos-dir JobId 11: Fatal error: Authorization key rejected by File Daemon bareos-dir.
19-5月 11:46 bareos-dir JobId 11: Fatal error: Unable to authenticate with File daemon at "192.168.0.8:9102". Possible causes:
Passwords or names not the same or
TLS negotiation failed or
Maximum Concurrent Jobs exceeded on the FD or
FD networking messed up (restart daemon).
19-5月 11:46 bareos-dir JobId 11: Fatal error: No Job status returned from FD.
19-5月 11:46 bareos-dir JobId 11: Error: Bareos bareos-dir 18.2.5 (30Jan19):
  Build OS:               Linux-4.4.92-6.18-default ubuntu Ubuntu 16.04 LTS
  JobId:                  11
  Job:                    backup-client2-fd.2019-05-19_11.46.06_04
  Backup Level:           Full (upgraded from Incremental)
  Client:                 "client2-fd" 18.2.5 (30Jan19) Microsoft Windows 8 Enterprise Edition (build 9200), 64-bit,Cross-compile,Win64
  FileSet:                "windows10" 2019-05-19 01:01:10
  Pool:                   "Full" (From Job FullPool override)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "File" (From Job resource)
  Scheduled time:         19-5月-2019 11:46:04
  Start time:             19-5月-2019 11:46:08
  End time:               19-5月-2019 11:46:53
  Elapsed time:           45 secs
  Priority:               10

  
```
## Problem to report
```
Terminated Jobs:
 JobId  Level    Files      Bytes   Status   Finished        Name 
======================================================================
     1  Full        353    42.65 M  OK       11-5月019 21:01 BackupClient1
     2  Incr          0         0   OK       12-5月019 14:54 BackupClient1
     3              353    42.65 M  OK       12-5月019 15:07 RestoreFiles
     4  Full        353    42.65 M  OK       18-5月019 21:01 backup-bareos-fd
     7  Incr          0         0   OK       19-5月019 00:46 backup-bareos-fd
    18  Incr          0         0   OK       19-5月019 15:16 backup-bareos-fd
====
You have messages.
*messages
19-5月 15:52 bareos-dir JobId 22: Connected Storage daemon at fred-Vostro-2420:9103, encryption: None
19-5月 15:52 bareos-dir JobId 22: Using Device "FileStorage2" to write.
19-5月 15:52 bareos-dir JobId 22: Probing client protocol... (result will be saved until config reload)
19-5月 15:52 bareos-dir JobId 22: Fatal error: Authorization key rejected by File Daemon bareos-dir.
19-5月 15:52 bareos-dir JobId 22: Fatal error: Unable to authenticate with File daemon at "192.168.0.8:9102". Possible causes:
Passwords or names not the same or
TLS negotiation failed or
Maximum Concurrent Jobs exceeded on the FD or
FD networking messed up (restart daemon).
19-5月 15:52 bareos-dir JobId 22: Fatal error: No Job status returned from FD.
19-5月 15:52 bareos-dir JobId 22: Error: Bareos bareos-dir 18.2.5 (30Jan19):
  Build OS:               Linux-4.4.92-6.18-default ubuntu Ubuntu 16.04 LTS
  JobId:                  22
  Job:                    backup-client2-fd.2019-05-19_15.51.38_04
  Backup Level:           Full (upgraded from Incremental)
  Client:                 "client2-fd" 18.2.5 (30Jan19) Microsoft Windows 8 Enterprise Edition (build 9200), 64-bit,Cross-compile,Win64
  FileSet:                "windows10" 2019-05-19 01:01:10
  Pool:                   "Full" (From Job FullPool override)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "File2" (From Job resource)
  Scheduled time:         19-5月-2019 15:51:36
  Start time:             19-5月-2019 15:51:40
  End time:               19-5月-2019 15:52:25
  Elapsed time:           45 secs
  Priority:               10
  FD Files Written:       0
  SD Files Written:       0
  FD Bytes Written:       0 (0 B)
  SD Bytes Written:       0 (0 B)
  Rate:                   0.0 KB/s
  Software Compression:   None
  VSS:                    no
  Encryption:             no
  Accurate:               no
  Volume name(s):         
  Volume Session Id:      1
  Volume Session Time:    1558252031
  Last Volume Bytes:      0 (0 B)
  Non-fatal FD errors:    1
  SD Errors:              0
  FD termination status:  Error
  SD termination status:  Waiting on FD
  FD  Secure Erase Cmd:   <NULL>
  Bareos binary info:     bareos.org build: Get official binaries and vendor support on bareos.com
  Termination:            *** Backup Error ***

19-5月 15:52 bareos-dir JobId 0: Fatal error: Authorization key rejected by File Daemon bareos-dir.
19-5月 15:52 bareos-dir JobId 0: Fatal error: Unable to authenticate with File daemon at "192.168.0.8:9102". Possible causes:
Passwords or names not the same or
TLS negotiation failed or
Maximum Concurrent Jobs exceeded on the FD or
FD networking messed up (restart daemon).
*estimate job=backup-client2-fd listing client=client2-fd fileset=windows10
Using Catalog "MyCatalog"
Connecting to Client client2-fd at 192.168.0.8:9102
Failed to connect to Client.
You have messages.
*messages
19-5月 15:58 bareos-dir JobId 0: Fatal error: Authorization key rejected by File Daemon bareos-dir.
19-5月 15:58 bareos-dir JobId 0: Fatal error: Unable to authenticate with File daemon at "192.168.0.8:9102". Possible causes:
Passwords or names not the same or
TLS negotiation failed or
Maximum Concurrent Jobs exceeded on the FD or
FD networking messed up (restart daemon).

```
