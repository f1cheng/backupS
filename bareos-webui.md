

## webui
```
root@fred-Vostro-2420:/etc/bareos-webui# ls -lrt
总用量 20
-rw-r--r-- 1 bareos bareos 1352 5月  18 12:52 configuration.ini
-rw-r--r-- 1 bareos bareos  382 5月  18 12:52 webui-admin.conf.back
-rw-r--r-- 1 bareos bareos 1980 5月  18 12:52 directors.ini.dpkg-old
-rw-r--r-- 1 bareos bareos  137 5月  18 15:36 admin.conf.back
-rw-r--r-- 1 bareos bareos 2193 5月  18 15:37 directors.ini
root@fred-Vostro-2420:/etc/bareos-webui# 

----
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# more admin.conf
#
# Restricted console used by bareos-webui
#
Console {
  Name = admin
  Password = admin
  Profile = "webui-admin"


  # As php does not support TLS-PSK,
  # and the director has TLS enabled by default,
  # we need to either disable TLS or setup
  # TLS with certificates.
  #
  # For testing purposes we disable it here
  TLS Enable = No-------------------------------------------------Key!!!! for access by admin/admin login, or can't.
}

root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# more admin.conf
#
# Restricted console used by bareos-webui
#
Console {
  Name = admin
  Password = admin
  Profile = "webui-admin"
  # As php does not support TLS-PSK,
  # and the director has TLS enabled by default,
  # we need to either disable TLS or setup
  # TLS with certificates.
  #
  # For testing purposes we disable it here
  TLS Enable = No----------------------------------
  #Command ACL = *all*
  CommandACL = run-----------------------------------after login, set here, then having access right to all menus.
  #JobACL = *all* 
}
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# 


root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# more bareos-mon.conf 
Console {
  Name = bareos-mon
  Description = "Restricted console used by tray-monitor to get the status of the director."
  Password = "PEQ+pVpueXv2l7g9qCkuJzMhpG8KcpTiODvMENaw+tNT"
  CommandACL = status, .status
  JobACL = *all*
}


```

## this item, removed, restart; add, restart; then access url.
```
  TLS Enable = No
}
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# vi admin.conf
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# service bareos-dir restart
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# vi admin.conf
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# service bareos-dir restart
root@fred-Vostro-2420:/etc/bareos/bareos-dir.d/console# http://192.168.0.4:81/bareos-webui/director/

```
