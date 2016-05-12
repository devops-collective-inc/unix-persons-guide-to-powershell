# commands detail - u

## unalias

````
remove-item -path alias:cdtemp
````

## uname

### uname -s


`uname -s` in Unix, according to the man page, gives the 'kernel-version' of the OS. This is the 'top-level version' of the Unix that you're on. Typical values are 'Linux', or 'AIX' or 'HP-UX'. So, on my laptop, typing `uname -s` gives:
````
Linux
````

I've only used this when writing a Unix script which have to do slightly different things on different flavours of unix.

Obviously, there's only one manufacturer for Windows software - Microsoft. So there's no direct equivalent to `uname -s`. The closest equivalent on Powershell would I think be:

get-wmiobject -class win32_operatingsystem | select caption

This returns:
````
caption
-------
Microsoft Windows 7 Professional
````
or
````
Microsoft Windows 8.1 Pro
````
or
````
Microsoft(R) Windows(R) Server 2003, Standard Edition
````
or
````
Microsoft Windows Server 2008 R2 Enterprise
````
or
````
Microsoft Windows Server 2012 Standard
````

### uname -n

According to the Linux help, uname -n does this:

````
       -n, --nodename
              print the network node hostname
````
So, typing uname -n gives


````
$ uname -n
nancy.one2one.co.uk
````

I haven't found a neat equivalent for this in Powershell, but this works:

````
get-wmiobject -class win32_computersystem  | select dnshostname, domain
````

The output is:

````
dnshostname                                                 domain
-----------                                                 ------
nancy                                                       one2one.co.uk
````

### uname -r

uname -r gives the kernel release in Unix. The output varies depending on the flavour of Unix - Wikipedia has a good list of examples

On my system uname -r gives:

````
2.6.32-200.20.1.el5uek:
````

The best Powershell equivalent would seem to be:

````
get-wmiobject -class win32_operatingsystem | select version
````

...which gives:

````
6.1.7601
````

The 7601 is Microsoft's build number.

### uname -v

uname -v typically gives the date of the unix build. As far a I can think, there isn't a Powershell equivalent

### uname -m

To be honest, I'm not entirely sure what uname -m shows us on Unix. The wikipedia page for uname shows various outputs none of which are hugely useful.

Running uname -m on my server gives:

````
x86_64
````

Is this a PowerShell equivalent?

````
$ get-ciminstance -class cim_computersystem | select SystemType
SystemType
----------
x64-based PC
````


## uptime
On most, but from memory possibly not all, flavours of *nix 'uptime' tells you how long the server has been up and running

````
$ uptime
 15:54:24 up 9 days,  5:43,  2 users,  load average: 0.10, 0.09, 0.07
````

A rough Powershell equivalent to show how long the server (or PC) has been running is:

````
get-wmiobject -class win32_operatingsystem  | select LastBootUpTime
````

....of course you can also do

````
get-wmiobject -class win32_operatingsystem -ComputerName some_other_server | 
    select LastBootUpTime
````

...to get the bootup time for a remote server, or PC.
