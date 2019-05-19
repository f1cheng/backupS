##
```
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
```
