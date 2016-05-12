# commands detail - c

## cal

There's no one-liner equivalent for the Linux `cal`, but there's a useful script, with much of the `cal` functionality here :

<a href="http://www.vistax64.com/powershell/17834-unix-cal-command.html">http://www.vistax64.com/powershell/17834-unix-cal-command.html</a>

## cd
The PowerShell equivalent of `cd` is:

````
Set-Location 
````

...although there is a builtin PowerShell alias `cd` which points at `set-location`

### cd ~
`cd ~` moves you to your home folder in both unix and Powershell.

## clear
The unix `clear` command clears your screen. The Powershell equivalent to the unix `clear` is

````
clear-host
````

PowerShell also has built-in alias `clear` for `clear-host`.

However, it's possibly worth noting that the behaviour of the two commands is slightly different between the two environments.

In my Linux environment, running putty, `clear` gives you a blank screen by effectively scrolling everything up, which means you can scroll it all back down.  

The Powershell `Clear-host` on the other hand seems to wipe the previous output (actually in the same way that cmd's `cls` command does....). This <i>could</i> be quite a significant difference, depending on what you want to clear and why!  

## cp

The Posh version of cp is

````
copy-item

````
The following are built-in aliases for copy-item:

````
cp
copy
````

## cp -R

To recursively copy:

````
copy -recurse
````

