
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
