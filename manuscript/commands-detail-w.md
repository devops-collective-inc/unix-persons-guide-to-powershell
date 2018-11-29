# commands detail - w

## wc -l 

~~~~~~~~
gc c:\temp\file.txt | measure-object | select count
~~~~~~~~

to show the number of <i>non-blank</i> lines:

~~~~~~~~
gc c:\temp\file.txt | measure-object -line
~~~~~~~~


## whoami

This shows the user that you are logged on as:

~~~~~~~~
[Security.Principal.WindowsIdentity]::GetCurrent() | select name
~~~~~~~~



## whence or type
There isn't a close equivalent to the unix `whence` command, because within Powershell there isn't a PATH variable for scripts. The environment's PATH and PSMODULEPATH list the folders for windows executables and for Powershell modules.

`get-command` shows the location of the windows executable, the name of the Powershell module or the translation of the alias, as follows:

~~~~~~~~
get-command whoami,Get-Command,invoke-sqlcmd,sserv,schtasks.exe | select name,version,source,DisplayName

Name          Version      Source                           DisplayName                      
----          -------      ------                           -----------                      
whoami.exe    10.0.17134.1 c:\windows\system32\whoami.exe                                    
Get-Command   3.0.0.0      Microsoft.PowerShell.Core                                         
Invoke-Sqlcmd 1.0          sqlps                                                             
sserv         0.0          WindowsStuff                     sserv -> show-nonstandardservices
schtasks.exe  10.0.17134.1 c:\windows\system32\schtasks.exe                                  

~~~~~~~~


