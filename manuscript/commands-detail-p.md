# commands detail - p

## ps

The PowerShell equivalent of the `ps` command is:

````
get-process
````


You can use `get-process` to get information about other computers:

````
get-process -ComputerName bigserver gvim*  
````

You can use `select` and `where` to 'slice and dice' the information.

````
get-process  | 
  where {$_.PeakWorkingSet -gt 1Mb } | select ProcessName,PeakWorkingSet

````


As with `ps`, the `get-process` command has many options.  This section of the e-book will be expanded over the next few months but, to start with, these are some of the `ps` examples from the Linux `man` page.

### ps -ef (see every process on the system)

By default `get-process` shows all of the processes on the current PC or server

### ps (show just current process)

If you wanted to just see details of your process you could do this:

````
get-process -pid $PID
````

`$PID` is an 'automatic variable' which contains the PID (process identifier) of the current process

For a list of automatic variables see <https://docs.microsoft.com/en-gb/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-6&viewFallbackFrom=powershell-Microsoft.PowerShell.Core> 



### ps -ejH (print a process tree)

There is no PowerShell equivalent to the Unix `ps -eJH`, because as I understand it Windows processes aren't part of a process tree.

### ps -eLf (get info about threads)
I _think_ this shows information about the processes threads:

````
get-process -pid $pid | select -expand threads
````

### ps -U (show particular user)

````
get-process -IncludeUserName | ? Username -eq "Ronnie\Matt"
````

## ps -ef | grep firefox 

````
get-process firefox
````


## pwd

To show your current location in Powershell:

````
Get-Location 
````

...or there are aliases `gl` and `pwd`.

There is also a built-in variable

````
$pwd
````


