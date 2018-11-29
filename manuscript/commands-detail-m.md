# commands detail - m

## mailx
To send an email from the PowerShell command line, this worked for me:

~~~~~~~~
$PSEmailServer = "exchange_server.domain.co.uk"
send-mailmessage -to eden.hazard@gmail.com -from matt@here.co.uk -subject "Hello"
~~~~~~~~

## man

The Powershell equivalent of `man` is:

~~~~~~~~
get-help 
~~~~~~~~

`get-help` has the following built-in aliases:

- `help`
- `man`

There are a couple of things to note about `get-help`.

There are two much-used options: `-full` and `-examples`. They both do what you'd expect, I think. To give some idea of scale, on my laptop `get-help get-process` currently returns just over a screenful of information, whereas `get-help -get-process -full` returns 9 screenfuls.

The help text can be brought up-to-date by running update-help from the command line.

You can easily write your own help text for your own functions, by using a feature called _comment-based help_.

## man -k

In \*nix `man -k` allows you to search through all the man pages for mentions of a particular keyword. It returns a list of the man pages which are relevant to the word you've searched for. On some systems, it's aliased to `apropos`. Anyway, `man -k disk` would perhaps return lines for, say, `du`, `df` and `lsvol` (at the time of typing I don't have a Linux install to hand, so I'm guessing here.)

There's no seperate command for this in PowerShell, because the `get-help` command does this by default if it doesn't find a direct match.

So, if you type `get-help get-process` you would get this:

~~~~~~~~
NAME
    Get-Process

SYNOPSIS
    Gets the processes that are running on the local computer or a remote computer.


SYNTAX
    Get-Process [[-Name] <String[]>] [-ComputerName <String[]>] [-FileVersionInfo] [-Module] [<CommonParameters>]

etc....
~~~~~~~~

...whereas if you typed `get-help process` you would get a list of help topics related to 'process'[1]:

~~~~~~~~
Name          Category Synopsis
----          -------- --------
Debug-Process Cmdlet   Debugs one or more processes running on the local computer.
Get-Process   Cmdlet   Gets the processes that are running on the local computer or a remote computer.
Start-Process Cmdlet   Starts one or more processes on the local computer.
Stop-Process  Cmdlet   Stops one or more running processes.
Wait-Process  Cmdlet   Waits for the processes to be stopped before accepting more input.

~~~~~~~~

## more

Powershell incorporates a `more` command which broadly works in the console similarly to the unix `more`. 

The Powershell `more` is a wrapper for `more.com`[2], which is an old Microsoft implementation of `more`.

`more` doesn't work in the ISE, but you can however easily scroll back through output by pressing 'Ctrl' and 'Up-arrow' at the same time. This then allows you to use all the arrow keys (as well as Ctrl-c and Ctrl-V to cut and paste) to navigate around the output from previous commands.

## mv

The PowerShell equivalent of `mv` is:

~~~~~~~~
Rename-Item 
~~~~~~~~

## Footnotes
---

[1] I actually did `get-help process | select name, category, synopsis | ft -a` to tidy up the output for the e-book.

[2] I found that in my current PowerShell installs, there wasn't much information on `more`.  The `get-help` command returned the barest of details.

To see what the command actually does I ran:

~~~~~~~~
get-command more | select definition | format-list
~~~~~~~~
