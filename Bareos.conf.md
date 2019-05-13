## conf
### test config files
```
5.4 Testing your Configuration Files
You can test if your configuration file is syntactically correct by running the appropriate daemon with the -t option. The daemon will process the configuration file and print any error messages then terminate.
As the Bareos Director and Bareos Storage Daemon runs as user bareos, testing the configuration should be done as bareos.
This is especially required to test the Bareos Director, as it also connects to the database and checks if the catalog schema version is correct. Depending on your database, only the bareos has permission to access it.
Commands 5.1: Testing Configuration Files
su bareos -s /bin/sh -c "/usr/sbin/bareos-dir -t"
su bareos -s /bin/sh -c "/usr/sbin/bareos-sd -t"
bareos-fd -t
bconsole -t
bareos-tray-monitor -t
```
### used by console
```

root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/director# more bareos-dir.conf 
Director {                            # define myself
  Name = bareos-dir
  QueryFile = "/usr/lib/bareos/scripts/query.sql"
  Maximum Concurrent Jobs = 10
  Password = "t77Wye8c5SH0ARkhEmiNZwT66kGeWhCG8I8S01fuLXbz"         # Console password
  Messages = Daemon
  TLS Enable = no
  TLS Require = no
  Auditing = yes

  # Enable the Heartbeat if you experience connection losses
  # (eg. because of your router or firewall configuration).
  # Additionally the Heartbeat can be enabled in bareos-sd and bareos-fd.
  #
  # Heartbeat Interval = 1 min

  # remove comment in next line to load dynamic backends from specified directory
  # Backend Directory = /usr/lib/bareos/backends

  # remove comment from "Plugin Directory" to load plugins from specified directory.
  # if "Plugin Names" is defined, only the specified plugins will be loaded,
  # otherwise all director plugins (*-dir.so) from the "Plugin Directory".
  #
  # Plugin Directory = /usr/lib/bareos/plugins
  # Plugin Names = ""
}
@/etc/bareos-webui/admin.conf 
@/etc/bareos-webui/webui-admin.conf
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/director# 



```
