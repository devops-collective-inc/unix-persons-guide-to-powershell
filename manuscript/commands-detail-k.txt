# commands detail - k

## kill

The equivalent of bash's `kill` is:
````
stop-process
````

A typical usage in Powershell might be:

````
# find the process
get-process | select id, ProcessName | where {$_.processname -like 'iex*'}

# kill the process
stop-process 5240
````

There is a built in alias `kill` which translates to stop-process

````
get-alias k*

CommandType     Name
-----------     ----
Alias           kill -> Stop-Process
````
