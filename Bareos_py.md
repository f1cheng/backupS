
# To access Bareos written in C.
## send command to Director(Bareos-dir daemon) to get result
### Python interface
```  
simulate bconsole via bconsole.py
==send_command or interactive in class LowLevel:
=>call(command)->__call(command)->send(command)->socket.sendall(..msg)

``` 
```python
    def interactive(self):
        """
        Enter the interactive mode.
        Exit via typing "exit" or "quit".
        """
        command = ""
        while command != "exit" and command != "quit" and self.is_connected():
            command = self._get_input()
            resultmsg = self.call(command)
            self._show_result(resultmsg)
        return True

```


### php interface
```
The similar way with python to accesing Bareos-dir daemon which is based on c language.
simulate bconsole.py via xxx.php
```

