# commands detail - e

## echo
`echo` is an alias in PowerShell. As you would expect it's an alias for the closest equivalent to the Linux `echo`:

- `write-output`

You use it as follows:
````
write-output "Blue is the colour"
````

As well as write-output there are a couple of options for use in Powershell scripts and functions:

- `write-debug`
- `write-verbose`

Whether these produce any output is controlled by commandline or environment flags. 


## echo -n
In bash, `echo -n` echoes back the string without printing a newline, so if you do this:

````
$ echo -n Blue is the colour
````

you get:

````
Blue is the colour$
````

....with your cursor ending up on the same line as the output, just after the dollar prompt

Powershell has an exact equivalent of 'echo -n'. If you type:

````
PS C:\Users\matt> write-host -nonewline "Blue is the colour"
````

....then you get this:


````
PS C:\Users\matt> write-host -nonewline "Blue is the colour"
Blue is the colourPS C:\Users\matt>
````

Note that `-nonewline` doesn't 'work' if you're in the ISE.

## egrep
The best PowerShell equivalent to `egrep` or `grep` is `select-string`:

````
select-string stamford blue_flag.txt
````

A nice feature of `select-string` which _isn't_ available in `grep` is the `-context` option. The -context switch allows you to see a specified number of lines either side of the matching one.  I think this is similar to `SEARCH /WINDOW` option in DCL.


## egrep -i 
Powershell is case-insensitive by default, so:

````
select-string stamford blue_flag.txt
````

...would return:
````
blue_flag.txt:3:From Stamford Bridge to Wembley
````

If you want to do a case sensitive search, then you can use:

````
select-string  -casesensitive stamford blue_flag.txt
````

## egrep -v
The Powershell equivalent to the `-v` option would be `-notmatch`

````
select-string -notmatch stamford blue_flag.txt
````

## egrep 'this|that'

To search for more than one string within a file in bash, you use the syntax:

````
egrep 'blue|stamford' blue_flag.txt
````

This will return lines which contain either 'blue' or 'stamford'.

The PowerShell equivalent is to seperate the two strings with a comma, so:

````
$ select-string  stamford,blue blue_flag.txt
````

...returns:


````
blue_flag.txt:2:We'll keep the blue flag flying high
blue_flag.txt:3:From Stamford Bridge to Wembley
blue_flag.txt:4:We'll keep the blue flag flying high 
````



## | egrep -i sql

This is an interesting one, in that it points up a conceptual difference between PowerShell and Bash.

In bash, if you want to pipe into a grep, you would do this:

````
ps -ef | egrep sql
````

This would show you all the processes which include the string 'sql' somewhere in the line returned by `ps`. The egrep is searching across the whole line. If the username is 'mr_sql' then a line would be returned, and if the process is 'sqlplus' than a line would also be returned.

To do something similar in PowerShell you would do something more specific

````
get-process | where processname -like '*sql*'
````

So the string 'sql' has to match the contents of the property `processname`. As it happens, get-process by default only returns one text field, so in this case it's relatively academic, but hopefully it illustrates the point.



## env
The Linux 'env' shows all the environment variables.

In PowerShell there are two set of environment variables:
- windows-level variables and
- Powershell-level variable

Windows-level variables are given by:

````
Get-ChildItem Env: | fl
````

PowerShell-level variables are given by:

````
get-variable
````

## errpt
I think errpt is possibly just an AIX thing (the linux equivalent is, I think, looking at `/var/log/message`). It shows system error and log messages.

The PowerShell equivalent would be to look at the Windows eventlog, as follows

````
get-eventlog -computername bigserver -logname application -newest 15 
````

The lognames that I typically look at are 'system', 'application' or 'security'.

## export PS1="$ "
In bash the following changes the prompt when you are at the command line

````
export PS1="$ "
````

The Powershell equivalent to this is:
````
function prompt {
 "$ "
 }
````

I found this on Richard Siddaway's blog: <http://msmvps.com/blogs/richardsiddaway/archive/2013/07/21/fun-with-prompts.aspx>

