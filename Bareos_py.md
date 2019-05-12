
# To access Bareos written in C.
## send command to Director(Bareos-dir daemon) to get result
### Python interface
```  
simulate bconsole via bconsole.py
==send_command or interactive in class LowLevel:
=>call(command)->__call(command)->send(command)->socket.sendall(..msg)
``` 

### php interface
```
The similar way with python to accesing Bareos-dir daemon which is based on c language.
simulate bconsole.py via xxx.php
```

