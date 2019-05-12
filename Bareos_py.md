# Python plugins usage

```
Bareos-dir-class-plugin.py (c:\work\personal\bareos\source\bareos-master\core\src\plugins\dird):
def load_bareos_plugin(context, plugindef):

```
```c
Python-dir.cc (c:\work\personal\bareos\source\bareos-master\core\src\plugins\dird):     
* Lookup the load_bareos_plugin() function in the python module.
Python-dir.cc (c:\work\personal\bareos\source\bareos-master\core\src\plugins\dird):                                 "load_bareos_plugin"); /* Borrowed reference */

dird main->RunJob(JobControlRecord* jcr)->
GeneratePluginEvent(jcr, bsdEventJobEnd)->
trigger_plugin_event->
handlePluginEvent(bpContext* ctx, bDirEvent* event, void* value)->
retval = PyLoadModule(ctx, plugin_options.c_str())->

    /*
     * Lookup the load_bareos_plugin() function in the python module.
     */
    pFunc = PyDict_GetItemString(p_ctx->pDict,
                                 "load_bareos_plugin"); /* Borrowed reference */
    if (pFunc && PyCallable_Check(pFunc)) {
      PyObject *pPluginDefinition, *pRetVal;

      pPluginDefinition = PyString_FromString((char*)value);
      if (!pPluginDefinition) { goto bail_out; }

      pRetVal = PyObject_CallFunctionObjArgs(pFunc, p_ctx->bpContext,
                                             pPluginDefinition, NULL);
                                             
```  

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

