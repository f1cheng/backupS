

## webui
```
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
  TLS Enable = No
  CommandACL = *all*
}

```
