# Todo

While the first version of this e-book is being written this list will be largely mechanical stuff which needs to be done to get the e-book into a suitable state. Subsequently it will be more a list of unix stuff for which I/we stilll need to find or document a PowerShell equivalent.


## for future versions

- look at http://blogs.technet.com/b/josebda/archive/2015/04/18/windows-powershell-equivalents-for-common-networking-commands-ipconfig-ping-nslookup.aspx

test conditions (not entirely sure that's the right unix terminology) - built
test conditions like if file exists and is not a directory, if variable exists
and is not null

pushd/popd

shutdown -r - restart-computer

more/less - remember it doesn't work in ISE

find - the various options. -newer, -exec

uname
uname options

crontab -l
cp -r
ls -R
.profile

bg
cp
cut

env
eval
file
find 
free (memory)
fuser filename
head

tee

/var/log/message
write
& (run in background)
PS1 (line contunuation prompt)
declare -F
type
Parameter passing
cut -f 3
for (p127)
while (p139)
until
case
select p113, p136
String comparisons p118
File attribute operations p122
fileinfo
Number comparisons p126
IFS (internal field separator) p127
PS3
getopts p145
let p145
arrays p160
here -documents p165
debugging stuff p221 
-n (syntax check)
-v
-x


For the section on ' | egrep -i' i.e. how to search for something within the pipeline, I've currently got instructions on how to use -like against a particular property. It would be good to have an alternative which did allow you to search across the whole output. Not very useful typically, but it would be nice to cover it off

export (variables)

my search history function

Mark L's comments
- would expect to see stuff like 'if-then-else' in the introductory pages
- would be worth looking at the man pages for bash itself (and perhaps for cmd)
- cover re-direction
- 'special variables' - $HOME, $PROFILE

More detail on invoke-locate ?

Cover Get-Item as well as Get-ChildItem for ls

Convert from gwmi to get-ciminstance

More on mailx/send-mailmessage

Think about whether to expand any and all aliases to the full command name


More on mv?

Fill out detail on the ps process tree option. All unix processes being
descendants of root, windows processes not necessarily being descendants of
anything

More on more :). More isn't an alias for out-host -paging

ps options - starting with those in the cygwin or bash help

ps -0 (get security info)
          ps -eo euser,ruser,suser,fuser,f,comm,label
          ps axZ
          ps -eM

....have been looking at the cim but not got anything much yet.  http://powershell.com/cs/blogs/tips/archive/2009/12/17/get-process-owners.aspx has wmi 

### ps -o
       To see every process with a user-defined format:
          ps -eo pid,tid,class,rtprio,ni,pri,psr,pcpu,stat,wchan:14,comm
          ps axo stat,euid,ruid,tty,tpgid,sess,pgrp,ppid,pid,pcpu,comm
          ps -eopid,tt,user,fname,tmout,f,wchan

### ps -C
       Print only the process IDs of syslogd:
          ps -C syslogd -o pid=

### ps -p
       Print only the name of PID 42:
          ps -p 42 -o comm=


rm options

rmdir

sort and sort -uniq - more detail on each

uptime - restore the 'sos' function etc....but work out what the approved verb would be for 'show'

who am i - as opposed to whoami. I think it shows the user you originally logged on as

the non-alphabetical stuff: \ and backtick

$ env | sort
_=/bin/env
CVS_RSH=ssh
G_BROKEN_FILENAMES=1
HISTSIZE=1000
HOME=/home/matt
HOSTNAME=whatever.co.uk
INPUTRC=/etc/inputrc
LANG=en_GB
LESSOPEN=|/usr/bin/lesspipe.sh %s
LOGNAME=matt
LS_COLORS=no=00:fi=00:di=00;34:ln=00;36:pi=40;33:so=00;35:bd=40;33;01:cd=40;33;01:or=01;05;37;41:mi=01;05;37;41:ex=00;32:*.cmd=00;32:*.exe=00;32:*.com=00;32:*.btm=00;32:*.bat=00;32:*.sh=00;32:*.csh=00;32:*.tar=00;31:*.tgz=00;31:*.arj=00;31:*.taz=00;31:*.lzh=00;31:*.zip=00;31:*.z=00;31:*.Z=00;31:*.gz=00;31:*.bz2=00;31:*.bz=00;31:*.tz=00;31:*.rpm=00;31:*.cpio=00;31:*.jpg=00;35:*.gif=00;35:*.bmp=00;35:*.xbm=00;35:*.xpm=00;35:*.png=00;35:*.tif=00;35:
MAIL=/var/spool/mail/matt
PATH=/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/home/matt/bin
PS1=$
PWD=/home/matt
SHELL=/bin/bash
SHLVL=1
SSH_TTY=/dev/pts/1
TERM=xterm

