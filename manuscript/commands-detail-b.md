# commands detail - b

## basename
A rough PowerShell equivalent for the unix _basename_ is:

~~~~~~~~
dir <whatever> | select name
~~~~~~~~

This depends on the file actually existing, whereas _basename_ doesn't care.
 
A more precise (but perhaps less concise) alternative[1] is:

~~~~~~~~
[System.IO.Path]::GetFileName('c:\temp\double_winners.txt')
~~~~~~~~


---
**Notes**
[1] I found `[System.IO.Path]::GetFileName` after reading [Power Tips of the Day - Useful Path Manipulations Shortcuts](http://powershell.com/cs/blogs/tips/archive/2014/09/08/useful-path-manipulation-shortcuts.aspx), which has some other useful commands

