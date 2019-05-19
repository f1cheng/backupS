
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
