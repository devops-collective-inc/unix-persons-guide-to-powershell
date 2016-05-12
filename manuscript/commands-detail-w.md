# commands detail - w

## wc -l 

````
gc c:\temp\file.txt | measure-object | select count
````

to show the number of <i>non-blank</i> lines:

````
gc c:\temp\file.txt | measure-object -line
````


## whoami

This shows user that you are logged on as:

````
[Security.Principal.WindowsIdentity]::GetCurrent() | select name
````



## whence or type
There isn't a single equivalent to the unix ````whence```` command, but there are a couple of things worth mentioning.

This shows the sort of thing (exe, bat, alias, function) that you're looking at:

````
get-command whoami

CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Application     whoami.exe
````

....and if what you're looking for is a file in your path, then this will find it 

````
foreach ($FOLDER in $ENV:PATH.split(";") ) { dir $FOLDER\whoami.exe -ea Si | select fullname }

FullName
--------
C:\Windows\system32\whoami.exe
````

This splits the path into its constituent folders, then does a _dir_ to see if
the file (in this case I'm looking for _whoami.exe_) exists in each.

