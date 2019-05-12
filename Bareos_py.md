# Python plugins usage

## python plugin
```
Bareos-dir-class-plugin.py (c:\work\personal\bareos\source\bareos-master\core\src\plugins\dird):
def load_bareos_plugin(context, plugindef):

(in c:   
static struct s_cmds cmds[] = {
    {"accurate", AccurateCmd, false},
    {"backup", BackupCmd, false},
->
BackupCmd(jcr)->GeneratePluginEvent(jcr, bEventStartBackupJob)

handlePluginEvent->PyHandlePluginEvent
)

bEventType = dict(
    bEventJobStart=1,
    bEventJobEnd=2,
    bEventStartBackupJob=3,
    ...
    
    def handle_plugin_event(self, context, event):
        if event == bEventType['bEventJobEnd']:
            bareosfd.DebugMessage(
                context, 100,
                "handle_plugin_event called with bEventJobEnd\n")

        elif event == bEventType['bEventEndBackupJob']:
            bareosfd.DebugMessage(
                context, 100,
                "handle_plugin_event called with bEventEndBackupJob\n")

        elif event == bEventType['bEventEndFileSet']:
            bareosfd.DebugMessage(
                context, 100,
                "handle_plugin_event called with bEventEndFileSet\n")

        elif event == bEventType['bEventStartBackupJob']:
            bareosfd.DebugMessage(
                context, 100,
                "handle_plugin_event() called with bEventStartBackupJob\n")

            return self.start_backup_job(context)


    ## real plugin using py to do the exact things.
    
    def start_backup_job(self, context):
        '''
        Start of Backup Job
        '''
        check_option_bRC = self.check_options(context)
        if check_option_bRC != bRCs['bRC_OK']:
            return check_option_bRC

        return self.ldap.prepare_backup(context, self.options)
        
```
## invoking py plugin in c  

```c 
Python-dir.cc (c:\work\personal\bareos\source\bareos-master\core\src\plugins\dird):   
* Lookup the load_bareos_plugin() function in the python module.
Python-dir.cc (c:\work\personal\bareos\source\bareos-master\core\src\plugins\dird):  
"load_bareos_plugin"); /* Borrowed reference */

dird main->RunJob(JobControlRecord* jcr)->
GeneratePluginEvent(jcr, bsdEventJobEnd)->
trigger_plugin_event->
handlePluginEvent(bpContext* ctx, bDirEvent* event, void* value)->
handlePluginEvent->

    switch (event->eventType) {
      case bDirEventNewPluginOptions:
        /*
         * See if we already loaded the Python modules.
         */
        if (!p_ctx->python_loaded) {
          retval = PyLoadModule(ctx, plugin_options.c_str());
        }

        /*
         * Only try to call when the loading succeeded.
         */
        if (retval == bRC_OK) {
          retval = PyParsePluginDefinition(ctx, plugin_options.c_str());
        }
        break;
      default:
        /*
         * Handle the generic events e.g. the ones which are just passed on.
         * We only try to call Python when we loaded the right module until
         * that time we pretend the call succeeded.
         */
        if (p_ctx->python_loaded) {
          retval = PyHandlePluginEvent(ctx, event, value);
==>
  pFunc = PyDict_GetItemString(p_ctx->pDict,
                               "handle_plugin_event"); /* Borrowed reference */
  if (pFunc && PyCallable_Check(pFunc)) {
    PyObject *pEventType, *pRetVal;

    pEventType = PyInt_FromLong(event->eventType);

    pRetVal =
        PyObject_CallFunctionObjArgs(pFunc, p_ctx->bpContext, pEventType, NULL);
    Py_DECREF(pEventType);
    
==> handle_plugin_event in Python    
     
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

