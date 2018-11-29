# commands summary
| Unix                               | Powershell                                                                                |
| -----------------------------------|-------------------------------------------------------------------------------------------|
| alias (set aliases)                | set-alias                                                                                 |
| alias (show aliases)               | get-alias                                                                                 |
| apropos                            | get-help                                                                                  |
| basename                           | dir \| select name                                                                        |
| cal                                | See commands detail                                                                       |
| cd                                 | cd                                                                                        |
| clear                              | clear-host                                                                                |
| date                               | get-date                                                                                  |
| date -s                            | set-date                                                                                  |
| df -k                              | Get-WMIObject Win32_LogicalDisk \| ft -a                                                  |
| diff                               | Compare-Object -ReferenceObject (Get-Content file1) -DifferenceObject (Get-Content file2) |
| dirname                            | dir \| select directory                                                                   |
| du                                 | See commands detail                                                                       |
| echo                               | write-output                                                                              |
| echo -n                            | write-host -nonewline                                                                     |
| \| egrep -i sql                    | \| where {[Regex]::Ismatch($\_.name.tolower(), "sql") }                                   |
| egrep -i                           | select-string                                                                             |
| egrep                              | select-string  -casesensitive                                                             |
| egrep -v                           | select-string -notmatch                                                                   |
| env                                | Get-ChildItem Env: \| fl  or  get-variable                                                |
| errpt                              | get-eventlog                                                                              |
| export PS1="$ "                    | function prompt {"$ " }                                                                   |
| find                               | dir  *whatever* -recurse                                                                  |
| for (start, stop, step)            | for ($i = 1; $i -le 5; $i++) {whatever}                                                   |
| head                               | gc file.txt \| select-object -first 10                                                    |
| history                            | get-history                                                                               |
| history \| egrep -i ls             | history \| select commandline \| where commandline -like '*ls*' \| fl                     |
| hostname                           | hostname                                                                                  |
| if-then-else                       | if  ( condition ) { do-this } elseif { do-that } else {do-theother}                       |
| if [ -f "$FileName" ]              | if (test-path $FileName)                                                                  |
| kill                               | stop-process                                                                              |
| less                               | more                                                                                      |
| locate                             | no equivalent but see link                                                                |
| ls                                 | get-childitem OR gci OR dir OR ls                                                         |
| ls -a                              | ls -force                                                                                 |
| lsusb                              | gwmi Win32_USBControllerDevice                                                            |
| mailx                              | send-mailmessage                                                                          |
| man                                | get-help                                                                                  |
| more                               | more                                                                                      |
| mv                                 | rename-item                                                                               |
| pg                                 | more                                                                                      |
| ps -ef                             | get-process                                                                               |
| ps -ef \| grep oracle              | get-process oracle                                                                        |
| pwd                                | get-location                                                                              |
| read                               | read-host                                                                                 |
| rm                                 | remove-item                                                                               |
| script                             | start-transcript                                                                          |
| sleep                              | start-sleep                                                                               |
| sort                               | sort-object                                                                               |
| sort -uniq                         | get-unique                                                                                |
| tail                               | gc file.txt \| select-object -last 10                                                     |
| tail -f                            | gc -tail 10 -wait file.txt                                                                |
| time                               | measure-command                                                                           |
| touch - create an empty file       | set-content -Path ./file.txt -Value $null                                                 |
| touch - update the modified date   | set-itemproperty -path ./file.txt -name LastWriteTime -value $(get-date)                  |
| wc -l                              | gc ./file.txt \| measure-object \| select count                                           |
| whoami                             | [Security.Principal.WindowsIdentity]::GetCurrent() \| select name                         |
| whence or type                     | No direct equivalent, but see link                                                        |
| unalias                            | remove-item -path alias:aliasname                                                         |
| uname -m                           | Get-WmiObject -Class Win32_ComputerSystem \| select manufacturer, model                   |
| uptime                             | get-wmiobject -class win32_operatingsystem \| select LastBootUpTime                       |
| \ (line continuation)              | ` (a backtick)                                                                            |






