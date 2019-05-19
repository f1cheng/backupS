
## try on other ubuntu or centos installation for Bareos Client testing.

## try  ports open
```
Console -> DIR:9101
DIR     -> SD:9103
DIR     -> FD:9102
FD      -> SD:9103

Note, port 9103 serves both the Director and the File daemon, each having its own independent connection.

If you are running iptables, you might add something like:

-A FW-1-INPUT -m state --state NEW -m tcp -p tcp --dport 9101:9103 -j ACCEPT
on your server, and

-A FW-1-INPUT -m state --state NEW -m tcp -p tcp --dport 9102 -j ACCEPT
```
