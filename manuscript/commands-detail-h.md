# commands detail - h

## head

The PowerShell equivalent of the \*nix `head` is:

````
gc file.txt | select-object -first 10
````

## history 

The Powershell equivalent of `history` is:

````
get-history 
````

There is a built in alias `history`

It's worth noting that history doesn't persist across PowerShell sessions, although if you search online there are a couple of published techniques for making it persistent.

It's also perhaps worth noting that Powershell gives you a couple of extra bits of information, if you want them:

````
get-history | gm -MemberType Property


   TypeName: Microsoft.PowerShell.Commands.HistoryInfo

Name               MemberType Definition                                                                 
----               ---------- ----------                                                                 
CommandLine        Property   string CommandLine {get;}                                                  
EndExecutionTime   Property   datetime EndExecutionTime {get;}                                           
ExecutionStatus    Property   System.Management.Automation.Runspaces.PipelineState ExecutionStatus {get;}
Id                 Property   long Id {get;}                                                             
StartExecutionTime Property   datetime StartExecutionTime {get;}       
````



## history | egrep -i ls

There is no direct equivalent of the shell functionality you get with `set -o vi` sadly. You can up- and down- arrow by default, but if you want to search through your history then you need to do something like this

````
history | select commandline | where-object {$_.commandline -like '*ls*'} 
````




## hostname

There is a windows `hostname` which does much the same thing as the Unix
`hostname`, but it's not Powershell. It's a standard-ish Windows executable that on my machine lives in c:\windows\system32

Details are here: <https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/hostname>

You can get the server name through PowerShell like this:

````
get-wmiobject -class win32_operatingsystem | select __SERVER
````

