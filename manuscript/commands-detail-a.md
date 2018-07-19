# commands detail - a

## alias (list all the aliases)
The Powershell equivalent of typing `alias` at the bash prompt is:

````
get-alias
````

## alias (set an alias)
At it's simplest, the powershell equivalent of the unix 'alias' when it's used
to set an alias is 'set-alias'

````
set-alias ss select-string
````

However, there's a slight wrinkle....

In unix, you can do this

````
alias bdump="cd /u01/app/oracle/admin/$ORACLE_SID/bdump/"
````

If you try doing this in Powershell, it doesn't work so well. If you do this:

````
set-alias cdtemp "cd c:\temp"

cdtemp
````

...then you get this error:

````
cdtemp : The term 'cd c:\temp' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.

At line:1 char:1

+ cdtemp

+ ~~~~~~

    + CategoryInfo          : ObjectNotFound: (cd c:\temp:String) [], 
    
    CommandNotFoundException
    
    + FullyQualifiedErrorId : CommandNotFoundException
````

A way around this is to create a function instead:

````
remove-item -path alias:cdtemp

function cdtemp {cd c:\temp}
````

You can then create an alias for the function:

````
set-alias cdt cdtemp
````

## apropos

`apropos` is one of my favourite bash commands, not so much for what it does...but because I like the word 'apropos'.

I'm not sure it exists on all flavours of *nix, but in bash `apropos` returns a list of all the man pages which have something to do with what you're searching for. If apropos isn't implemented on your system you can use `man -k` instead.

Anyway on bash, if you type:


````
apropos process
````
...then you get:

````
AF_LOCAL [unix]      (7)  - Sockets for local interprocess communication

AF_UNIX [unix]       (7)  - Sockets for local interprocess communication

Apache2::Process     (3pm)  - Perl API for Apache process record

BSD::Resource        (3pm)  - BSD process resource limit and priority functions

CPU_CLR [sched_setaffinity] (2)  - set and get a process's CPU affinity mask

CPU_ISSET [sched_setaffinity] (2)  - set and get a process's CPU affinity mask

CPU_SET [sched_setaffinity] (2)  - set and get a process's CPU affinity mask

CPU_ZERO [sched_setaffinity] (2)  - set and get a process's CPU affinity mask

GConf2              (rpm) - A process-transparent configuration system

````

The Powershell equivalent of `apropos` or `man -k` is simply `get-help`

````
get-help process

Name                  Category  Module     Synopsis

----                  --------  ------     --------

get-dbprocesses       Function             Get processes for a particul...

show-dbprocesses      Function             Show processes for a particu...

Debug-Process         Cmdlet    Microso... Debugs one or more processes...

Get-Process           Cmdlet    Microso... Gets the processes that are ...
````

This is quite a nice feature of PowerShell compared to Bash. If `get-help` in Powershell shell scores a 'direct hit' (i.e. you type something like `get-help debug-process`) it will show you the help for that particular function. If you type something more vague, it will show you a list of all the help pages you might be interested in.

By contrast if you typed `man process` at the Bash prompt, you'd just get

````
No manual entry for process
```` 
