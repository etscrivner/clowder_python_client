# Clowder Python Client

This is the python repository for the Clowder python client.

### How to install
```
sudo pip install https://github.com/keithhackbarth/clowder_client/zipball/master
```


### How to test

Basic example for tracking memory usage on server
Create a python file memory_usage.py

```
import clowder
import psutil

clowder.api_key = '29rTtCyrBfZvABBMMbne'

clowder.ok({
   'name': 'Memory Utilization',
   'value': psutil.phymem_usage().percent
})
```

### How to use

Run the file and make sure it works

```
python memory_usage.py
```

Then create a cron job to run every 5 minutes

```
*/5 * * * * python memory_usage.py
```

### Parameters

Passed as python dictionary

- *name*: (string - REQUIRED) A unique name for the check. All checks with this name will be combined.
- *url*: (string - optional) The url to send data to. Defaults to www.clowder.io
- *value*: (float - optional) The value of the check (such as response time, queue length, rows processed, etc.)
- *status*: (integer - optional) Whether our not the check is passing (1, 0, -1). If failing, an alert is send.
- *frequency*: (integer - optional) Duration in minutes until next check. If time passes without check, alert sounds.
- *alert*: (function - optional) A lamdba function that passes or fails based on *value*

