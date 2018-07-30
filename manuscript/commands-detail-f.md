# commands detail - f

## find
The bash `find` command has loads of functionality - I could possibly devote many pages to Powershell equivalents of the various options, but at it's simplest the bash `find` does this:

````

find . -name '*BB.txt'

./Archive/Script_WO7171BB.txt

./Archive/Script_WO8541BB.txt

./Archive/Script_WO8645_BB.txt

./Archive/WO8559B/Script_WO8559_Master_ScriptBB.txt

./Archive/WO8559B/WO8559_finalBB.txt

./Archive/WO8559B/WO8559_part1BB.txt

./Archive/WO8559B/WO8559_part2BB.txt

````

The simplest Powershell equivalent of the bash `find` is simply to stick a `-recurse` on the end of a `dir` command

````

PS x:\> dir  *BB.txt -recurse

    Directory: x:\Archive\WO8559B

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-----        28/02/2012     17:15        608 Script_WO8559_Master_ScriptBB.txt
-----        28/02/2012     17:17         44 WO8559_finalBB.txt
-----        28/02/2012     17:17      14567 WO8559_part1BB.txt
-----        28/02/2012     17:15       1961 WO8559_part2BB.txt

    Directory: x:\Archive

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-----        15/06/2011     08:56       2972 Script_WO7171BB.txt
-----        14/02/2012     16:39       3662 Script_WO8541BB.txt
-----        27/02/2012     15:22       3839 Script_WO8645_BB.txt
````

If you want Powersehll to give you output that looks more like the Unix find then you can pipe into `| select fullname`


````
PS x:\> dir  *BB.txt -recurse | select fullname

FullName
--------
x:\Archive\WO8559B\Script_WO8559_Master_ScriptBB.txt
x:\Archive\WO8559B\WO8559_finalBB.txt
x:\Archive\WO8559B\WO8559_part1BB.txt
x:\Archive\WO8559B\WO8559_part2BB.txt
x:\Archive\Script_WO7171BB.txt
x:\Archive\Script_WO8541BB.txt
x:\Archive\Script_WO8645_BB.txt
````

## for

### for loop - start, stop, step
The equivalent of this bash:

````
for (( i = 1 ; i <= 5 ; i++ ))
do   
  echo "Hello, world $i"
done

Hello, world 1
Hello, world 2
Hello, world 3
Hello, world 4
Hello, world 5

````
...is

````
for ($i = 1; $i -le 5; $i++)
{
  write-output "Hello, world $i"
}

Hello, world 1
Hello, world 2
Hello, world 3
Hello, world 4
Hello, world 5
````


### for loop - foreach item in a list
For the Bash
````
for I in Chelsea Arsenal Spuds
do
  echo $I
done
````
the equivalent Powershell is:
````
foreach ($Team in ("Chelsea", "Arsenal", "Spuds")) {write-output $Team}
````

### for loop - for each word in a string
For the bash:

````
london="Chelsea Arsenal Spurs"
for team in $london; do   echo "$team"; done
````
...the equivalent Powershell is:

````
$London = "Chelsea Arsenal Spuds"
foreach ($Team in ($London.split())) {write-output $Team}
````

### for loops - for lines in a file
Bash:

````
for team in $(egrep -v mill london.txt)
> do
>   echo $team
> done
````

Posh:

````
select-string -notmatch millwall london.txt | select line | foreach {write-output $_}
````
or:

````
foreach ($team in (select-string -notmatch millwall london.txt | select line)) {$team}
````

### for loop - for each file in a folder</h4>
Bash:

````
for LocalFile in *
do   
  echo $LocalFile
done
````
Posh:

````
foreach ($LocalFile in $(gci)) {write-output $LocalFile.Name}
````




