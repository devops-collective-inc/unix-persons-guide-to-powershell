# commands detail - s

##  script 

````
start-transcript 
````

## sleep  

````
start-sleep -seconds 5
````

or 

````
start-sleep -milliseconds 250
````

or just:

````
sleep 3
````

...will sleep for 3 seconds



## sort  

````
get-process | sort-object -property VirtualMemorySize
````


## sort -u

The closest PowerShell equivalent to the unix `sort -u` is `get-unique`

````
gc c:\temp\2000.txt | sort | gu
````

Note: this only works as far I can see if you sort it first

Note 2: get-unique IS case sensitive


## sql

This isn't really a Powershell equivalent of a unix command, but in case it's useful, to call Sqlserver's implementation of the sql command line from Powershell you can use `invoke-sqlcmd`

````
Invoke-Sqlcmd -ServerInstance -query "Select blah" -database _catalog 
````

You need to have the sql module loaded for this to work, or be running the Powershell console from within SSMS
