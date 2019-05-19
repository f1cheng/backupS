##
```
FeideMacBook-Pro:client root# pwd
/usr/local/etc/bareos/bareos-fd.d/client
FeideMacBook-Pro:client root# 
FeideMacBook-Pro:client root# 


FeideMacBook-Pro:director root# launchctl list org.bareos.bareos-fd
{
	"StandardOutPath" = "/var/run/bareos-fd.log";
	"LimitLoadToSessionType" = "System";
	"StandardErrorPath" = "/var/run/bareos.log";
	"Label" = "org.bareos.bareos-fd";
	"TimeOut" = 30;
	"OnDemand" = true;
	"LastExitStatus" = 0;
	"PID" = 2164;
	"Program" = "/usr/local/sbin/bareos-fd";
	"ProgramArguments" = (
		"/usr/local/sbin/bareos-fd";
		"-f";
	);
};
FeideMacBook-Pro:director root# 


run

*estimate job=backup-client4-fd listing client=client4-fd fileset=macos


19-5月 20:32 bareos-dir JobId 33: No prior Full backup Job record found.
19-5月 20:32 bareos-dir JobId 33: No prior or suitable Full backup found in catalog. Doing FULL backup.
19-5月 20:32 bareos-dir JobId 33: Start Backup JobId 33, Job=backup-client4-fd.2019-05-19_20.32.31_04
19-5月 20:32 bareos-dir JobId 33: Connected Storage daemon at fred-Vostro-2420:9103, encryption: None
19-5月 20:32 bareos-dir JobId 33: Using Device "FileStorageMacos" to write.
19-5月 20:35 bareos-dir JobId 33: Warning: lib/bsock_tcp.cc:133 Could not connect to Client: client4-fd on 192.168.0.10:9102. ERR=被中断的系统调用
Retrying ...
19-5月 20:36 bareos-dir JobId 33: Fatal error: lib/bsock_tcp.cc:139 Unable to connect to Client: client4-fd on 192.168.0.10:9102. ERR=被中断的系统调用
19-5月 20:36 bareos-dir JobId 33: Fatal error: 
Failed to connect to client "client4-fd".
19-5月 20:36 bareos-dir JobId 33: Fatal error: No Job status returned from FD.
19-5月 20:36 bareos-dir JobId 33: Error: Bareos bareos-dir 18.2.5 (30Jan19):
  Build OS:               Linux-4.4.92-6.18-default ubuntu Ubuntu 16.04 LTS
  JobId:                  33
  Job:                    backup-client4-fd.2019-05-19_20.32.31_04
  Backup Level:           Full (upgraded from Incremental)
  Client:                 "client4-fd" 17.2.4 (21Sep17) x86_64-apple-darwin14.5.0,osx,14.5.0
  FileSet:                "macos" 2019-05-19 20:03:45
  Pool:                   "Full" (From Job FullPool override)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "FileMacos" (From Job resource)
  Scheduled time:         19-5月-2019 20:32:28
  Start time:             19-5月-2019 20:32:34
  End time:               19-5月-2019 20:36:24
  Elapsed time:           3 mins 50 secs
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
  Volume Session Time:    1558268679
  Last Volume Bytes:      0 (0 B)
  Non-fatal FD errors:    1
  SD Errors:              0
  FD termination status:  Error
  SD termination status:  Waiting on FD
  FD  Secure Erase Cmd:   <NULL>
  Bareos binary info:     bareos.org build: Get official binaries and vendor support on bareos.com
  Termination:            *** Backup Error ***

19-5月 20:36 bareos-dir JobId 0: Fatal error: 
Failed to connect to client "client4-fd".
19-5月 20:36 bareos-dir JobId 0: Fatal error: 
Failed to connect to client "client3-fd".
19-5月 20:37 bareos-dir JobId 0: Fatal error: 
Failed to connect to client "client2-fd".
19-5月 20:44 bareos-dir JobId 34: No prior Full backup Job record found.
19-5月 20:44 bareos-dir JobId 34: No prior or suitable Full backup found in catalog. Doing FULL backup.
19-5月 20:45 bareos-dir JobId 34: Start Backup JobId 34, Job=backup-client4-fd.2019-05-19_20.44.59_07
```
