# commands detail - t

## tail

````
gc file.txt | select-object -last 10
````

`gc` is an alias for `get-command`

## tail -f

````
gc -tail 10 -wait c:\windows\windowsupdate.log 
````

## tee

The Powershell equivalent of the unix `tee` is `tee-object`....which, by default is aliased to `tee`

So you can do this:

````
get-process | tee c:\temp\test_tee.txt
````

...to both get a list of processes on your screen and get that output saved into the file in c:\temp


## time

The Powershell equivalent of the bash shell 'time' is 'measure-command'.

So, in bash you would do this:

````
time egrep ORA- *log
````

....and get all the egrep output, then

````
real    0m4.649s
user    0m0.030s
sys     0m0.112s

````

In Powershell, you would do this

````
measure-command {select-string ORA- *.sql}

````

...and get...

````
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 105
Ticks             : 1057357
TotalDays         : 1.22379282407407E-06
TotalHours        : 2.93710277777778E-05
TotalMinutes      : 0.00176226166666667
TotalSeconds      : 0.1057357
TotalMilliseconds : 105.7357

````

...you don't get the 'user CPU' time and 'system CPU' time, but you do get the added bonus of seeing how long the command took rendered as a fraction of a day!



## touch - create an empty file

````
set-content -Path c:\temp\new_empty_file.dat -Value $null
````

I found the set-content command at <a href="http://superuser.com/questions/502374/equivalent-of-linux-touch-to-create-an-empty-file-with-powershell">Super User</a>, the contributor being <a href="http://superuser.com/users/23133/techie007">user techie007</a>

## touch - update the modified date

````
set-itemproperty -path c:\temp\new_empty_file.dat -name LastWriteTime -value $(get-date)
````
I got this from a comment by <a href="https://twitter.com/manung">Manung Han</a> on the <a href="http://blog.lab49.com/archives/249#comment-1076">Lab49 Blog</a>. Doug Finke shares <a href="http://blog.lab49.com/archives/249">touch function</a> in a later comment on the same post that fully implements the linux command.

