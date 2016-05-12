# commands detail - l

## locate

There isn't a builtin PowerShell version of locate, but Chrissy LeMaire's (<a href="http://blog.netnerds.net">website</a>) has written an <a href="https://gallery.technet.microsoft.com/scriptcenter/Invoke-Locate-PowerShell-0aa2673a">Invoke-Locate script</a> 'in the spirit of (Linux/Unix) GNU findutils' locate'. It works really well


## ls

The PowerShell equivalent of the Unix _ls_ is:

````
Get-ChildItem 
````

... for which there are aliases _dir_, _ls_ and _gci_

#### ls -a

In linux, _ls -a_ displays hidden files as well as 'normal' files.

So _ls_ gives:

````
$ ls
README.md
````
but _ls -a_ gives

````
$ ls -a
.  ..  .function-prompt.ps1.swp  .git  README.md

````

The Powershell equivalent of _ls -a_ is _get-childitem -force_. Here, I've used the alias _ls_

````
$ ls


    Directory: C:\Users\matt\Documents\WindowsPowerShell\functions


Mode                LastWriteTime     Length Name  
----                -------------     ------ ---- 
-a---        04/06/2015     13:20       1422 README.md



$ ls -force


    Directory: C:\Users\matt\Documents\WindowsPowerShell\functions


Mode                LastWriteTime     Length Name               
----                -------------     ------ ----              
d--h-        04/06/2015     13:20            .git             
-a-h-        20/05/2015     17:33      12288 .function-prompt.ps1.swp
-a---        04/06/2015     13:20       1422 README.md              

````

#### ls -ltr
The Powershell equivalent of the unix _ls -ltr_ (or the DOS _dir /OD_), which
lists files last update order.

````
dir c:\folder | sort-object -property lastwritetime
````


## lsusb
The unix command _lsusb_ shows USB devices. The PowerShell equivalent is:

````
gwmi Win32_USBControllerDevice
````

_gwmi_ is an alias for _get-wmiobject_

