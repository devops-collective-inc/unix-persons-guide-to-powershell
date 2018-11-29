# commands detail - i

## if-then-else

The bash `if-then-elif-else` as per:

~~~~~~~~
HOUR_OF_DAY=$(date +'%H') 

if  [ $HOUR_OF_DAY -lt 6 ]
then  
  echo  "Still nightime"
elif [ $HOUR_OF_DAY -lt 12 ]
then
  echo "Morning has broken"
elif [ $HOUR_OF_DAY -lt 18 ]
then
  echo "After noon"
else
  echo "Nightime again"
fi
~~~~~~~~

...could be rendered in PowerShell as:

~~~~~~~~
[int]$HourOfDay = $(get-date -UFormat '%H')

if  ( $HourOfDay -lt 6 )
{
  write-output  "Still nightime"
}
elseif ( $HourOfDay -lt 12 )
{
  write-output "Morning has broken"
}
elseif ( $HourOfDay -lt 18 )
{
  write-output "After noon"
}
else
{
  write-output "Nightime again"
}
~~~~~~~~

## if [ -f "$FileName" ]

Testing for the existence of a file in bash is done as follows

~~~~~~~~
export FileName=~/.matt
if [ -f "$FileName" ]
then
  echo "$FileName found."
else
  echo "$FileName not found."
fi
~~~~~~~~

In PowerShell this could be[1]

~~~~~~~~
$FileName = "c:\powershell\.matt.ps1x"
if (test-path $FileName) 
  {echo "$FileName found"}
else
  {echo "$FileName not found"}
~~~~~~~~

## Footnotes

[1] The way I've rendered the PowerShell here isn't great, but I've left it like that for a couple of reasons. First, it shows the similarity between PowerShell and Bash, which I think is encouraging for anyone reading this e-book. Second it allows me make this brief point about using aliases.  

`echo` is handy. It's short, and it looks like it does the same thing as `echo` in Unix, MS-DOS and probably a few other languages besides. It pretty much does...but does `echo` alias `write-output` which allows you to pipe to other PowerShell commands, or does it alias to `write-host`, which doesn't?

I've been using PowerShell for a few years now but I didn't know. I had to look it up. This is extra hassle if you're reading a script, which is one of the reasons that it's usually seen as being better practice in scripts to be explicit by using the full command rather than the alias.

Also, in PowerShell scripts rather than this:

~~~~~~~~
if (test-path $FileName) 
  {write-host "$FileName found"}
~~~~~~~~

...it would typically be seen as better to format using one of these two alternatives:

~~~~~~~~
if (test-path $FileName) {
  write-host "$FileName found"
}
~~~~~~~~
or:

~~~~~~~~
if (test-path $FileName) 
{
  write-host "$FileName found"
}
~~~~~~~~


