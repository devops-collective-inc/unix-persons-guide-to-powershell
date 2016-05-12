# commands summary

## alias (set aliases) 

````
set-alias 
````
[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-a.txt) 

## alias (show aliases) 

````
get-alias 
````
[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-a.txt) 

## apropos 

````
get-help 
````
[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-a.txt) 

## basename 

````
dir | select name 
````
[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-b.txt) 

## cal 

No equivalent, but see the script at <a href="http://www.vistax64.com/powershell/17834-unix-cal-command.html">http://www.vistax64.com/powershell/17834-unix-cal-command.html</a>


## cd 

````
cd 
````
[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-c.txt) 

## clear 

````
clear-host 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-c.txt) 

## date 

````
get-date 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-d.txt) 

## date -s 

````
set-date 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-d.txt) 

## df -k 

````
Get-WMIObject Win32_LogicalDisk | ft -a  
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-d.txt) 

## diff
````
Compare-Object -ReferenceObject (Get-Content file1) -DifferenceObject (Get-Content file2)
````

## dirname 

````
dir | select directory 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-d.txt) 

## du 

No equivalent, but see the [link](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-d.txt) 

## echo 

````
write-output 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## echo -n 

````
write-host -nonewline 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## | egrep -i sql 

````
 | where {[Regex]::Ismatch($\_.name.tolower(), "sql") } 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## egrep -i 

````
select-string 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## egrep  

````
select-string  -casesensitive 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## egrep -v 

````
select-string -notmatch 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## env 

````
Get-ChildItem Env: | fl 
````
or
````
get-variable 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## errpt 

````
get-eventlog 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## export PS1=”$ “ 

````
function prompt {"$ " } 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-e.txt) 

## find 

````
dir  *whatever* -recurse 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-f.txt) 

## for (start, stop, step) 

````
for ($i = 1; $i -le 5; $i++) {whatever} 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-f.txt) 

## head 

````
gc file.txt | select-object -first 10 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-h.txt) 

## history 

````
get-history 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-h.txt) 

## history | egrep -i ls 

````
history | select commandline | where commandline -like '*ls*' | fl 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-h.txt) 

## hostname 

````
hostname 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-h.txt) 

## if-then-else 

````
if  ( condition ) { do-this } elseif { do-that } else {do-theother}  
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-i.txt) 

## if [ -f "$FileName" ] 

````
if (test-path $FileName) 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-i.txt) 

## kill 

````
stop-process 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-k.txt) 

## less

````
more
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-m.txt) 

## locate 

````
no equivalent but see link 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-l.txt) 

## ls 

````
get-childitem OR gci OR dir OR ls 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-l.txt) 

## ls -a

````
ls -force 
````
[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-l.txt) 

## ls -ltr 

````
dir c:\ | sort-object -property lastwritetime 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-l.txt) 

## lsusb 

````
gwmi Win32_USBControllerDevice 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-l.txt) 

## mailx 

````
send-mailmessage 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-m.txt) 

## man 

````
get-help 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-m.txt) 

## more

````
more
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-m.txt) 


## mv 

````
rename-item 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-m.txt) 

## pg

````
more
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-m.txt) 


## ps -ef 

````
get-process 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-p.txt) 

## ps -ef | grep oracle 

````
get-process oracle 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-p.txt) 

## pwd 

````
get-location 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-p.txt) 

## read 

````
read-host 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-r.txt) 

## rm 

````
remove-item 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-r.txt) 

## script 

````
start-transcript 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-s.txt) 

## sleep 

````
start-sleep 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-s.txt) 

## sort 

````
sort-object 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-s.txt) 

## sort -uniq 

````
get-unique 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-s.txt) 

## tail 

````
gc file.txt | select-object -last 10 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-t.txt) 

## tail -f 

````
gc -tail 10 -wait file.txt 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-t.txt) 

## time 

````
measure-command 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-t.txt) 

## touch - create an empty file 

````
set-content -Path ./file.txt -Value $null 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-t.txt) 

## touch - update the modified date 

````
set-itemproperty -path ./file.txt -name LastWriteTime -value $(get-date) 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-t.txt) 

## wc -l 

````
gc ./file.txt | measure-object | select count 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-w.txt) 

## whoami 

````
[Security.Principal.WindowsIdentity]::GetCurrent() | select name 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-w.txt) 

## whence or type 

````
No direct equivalent, but see link 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-w.txt) 

## unalias 

````
remove-item -path alias:aliasname 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-u.txt) 

## uname -m 

````
Get-WmiObject -Class Win32_ComputerSystem | select manufacturer, model 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-u.txt) 

## uptime 

````
get-wmiobject -class win32_operatingsystem | select LastBootUpTime` 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-u.txt) 

## \ (line continuation) 

````
` (a backtick) 
````

[More](https://www.penflip.com/powershellorg/a-unix-persons-guide-to-powershell/blob/master/commands-detail-non-alphabetical.txt) 






