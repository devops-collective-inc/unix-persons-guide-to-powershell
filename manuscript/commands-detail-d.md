# commands detail - d

## date

The Powershell equivalent of the Unix `date` is

~~~~~~~~
get-date 
~~~~~~~~

The Powershell equivalent of the Unix `date -s` is

~~~~~~~~
set-date
~~~~~~~~

I was anticipating doing a fairly tedious exercise of going through all the Unix date formats and then working out the Powershell equivalent, but discovered the Powershell Team has effectively done all this for me. There is a Powershell option  `-UFormat` which stands for 'unix format'. 

So the Powershell:

~~~~~~~~
date -Uformat '%D'

09/08/14
~~~~~~~~

is the same as the *nix

~~~~~~~~
date +'%D'

09/08/14
~~~~~~~~

This is handy...but I have found the odd difference. I tried this for a demo:

Unix:

~~~~~~~~
date +'Today is %A the %d of %B, the %V week of the year %Y. My timezone is %Z, and here it is %R'

Today is Monday the 08 of September, the 37 week of the year 2014. My timezone is BST, and here it is 17:24
~~~~~~~~

Powershell:

~~~~~~~~
get-date -Uformat 'Today is %A the %d of %B, the %V week of the year %Y. My timezone is %Z, and here it is %R'

Today is Monday the 08 of September, the 36 week of the year 2014. My timezone is +01, and here it is 17:25
~~~~~~~~

I presume the discrepancy in the week of the year is to do with when the week turns - as you can see I ran the command on a Monday. Some systems have the turn of the week being Monday, others have it on Sunday.

I don't know why `%Z` outputs different things....and I can't help feeling I'm being churlish pointing this out. The -UFormat option is a really _nice_ thing to have.


## df -k
A quick and dirty Powershell equivalent to 'df -k' is

~~~~~~~~
Get-WMIObject Win32_LogicalDisk -filter "DriveType=3" | ft
~~~~~~~~

A slightly prettier version is this function:

~~~~~~~~
function get-serversize { Param( [String] $ComputerName)


Get-WMIObject Win32_LogicalDisk -filter "DriveType=3" -computer $ComputerName | 

   Select SystemName, DeviceID, VolumeName,

          @{Name="size (GB)";Expression={"{0:N1}" -f($_.size/1gb)}},

          @{Name="freespace (GB)";Expression={"{0:N1}" -f($_.freespace/1gb)}} 

}


function ss { Param( [String] $ComputerName)

    get-serversize $ComputerName | ft

}

~~~~~~~~ 

....then you can just do:

~~~~~~~~
$ ss my_server 
~~~~~~~~

....and get

~~~~~~~~
SystemName   DeviceID    VolumeName     size(GB)          freespace(GB)

----------   --------    ----------     --------          -------------

my_server    C:          OS             30.0                        7.8

my_server    D:          App            250.0                       9.3

my_server    E:                         40.0                        5.0

~~~~~~~~


## dirname

A good PowerShell equivalent to the unix `dirname` is 

~~~~~~~~
gi c:\double_winners\chelsea.doc | select directory
~~~~~~~~

However, this isn't a _direct_ equivalent. Here, I'm telling Powershell to look at an actual file and then return that file's directory. The file has to exist. The unix 'dirname' doesn't care whether the file you specify exists or not. 

If you type in `dirname /tmp/double_winners/chelsea.doc` on _any_ Unix server it will return `/tmp/double_winners`, I think. `dirname` is essentially a string-manipulation command. 

A more precise Powershell equivalent to the unix 'dirname' is this

~~~~~~~~
[System.IO.Path]::GetDirectoryName('c:\double_winners\chelsea.doc')
~~~~~~~~

....but it's not as easy to type, and 9 times out of 10 I do want to get the folder for an existing file rather than an imaginary one.

## du

While I think there _are_ implementations of `du` in PowerShell, personally my recommendation would be to download Mark Russinovich's 'du' tool, which is here:


<http://technet.microsoft.com/en-us/sysinternals/bb896651.aspx>

This is part of the Microsoft's 'sysinternals' suite.
