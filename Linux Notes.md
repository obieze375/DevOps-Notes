

# Git Aliases
~~~~
alias ga='git add' 

alias gaa='git add .' 

alias gaaa='git add --all' 

alias gau='git add --update' 

alias gb='git branch' 

alias gbd='git branch --delete ' 

alias gc='git commit' 

alias gcm='git commit --message' 

alias gcf='git commit --fixup' 

alias gco='git checkout' 

alias gcob='git checkout -b' 

alias gcom='git checkout master' 

alias gcos='git checkout staging' 

alias gcod='git checkout develop'  

alias gd='git diff'  

alias gda='git diff HEAD'  

alias gi='git init'  

alias glg='git log --graph --oneline --decorate --all'  

alias gld='git log --pretty=format:"%h %ad %s" --date=short --all' 

alias gm='git merge --no-ff'  

alias gma='git merge --abort'  

alias gmc='git merge --continue' 

alias gp='git pull'   

alias gpr='git pull --rebase'  

alias gr='git rebase'  

alias gs='git status'   

alias gss='git status --short'  

alias gst='git stash'  

alias gsta='git stash apply'  

alias gstd='git stash drop'  

alias gstl='git stash list'  

alias gstp='git stash pop'  

alias gsts='git stash save'
~~~~


# Git Functions


# Git log find by commit message

~~~~
function glf() { git log --all --grep="$1"; } 

~~~~

From <https://jonsuh.com/blog/git-command-line-shortcuts/>  


# How to create aliases


# Git log find by commit me

~~~~
1. Edit ~/.bash_aliases or ~/.bashrc file using: vi ~/.bash_aliases
2. Append your bash alias
3. For example append: alias update='sudo yum update'
4. Save and close the file.
5. Activate alias by typing: source ~/.bash_aliases 
~~~~

Please note that ~/.bash_aliases file only works if the following line presents in the ~/.bashrc file: 
~~~~
if [ -f ~/.bash_aliases ]; then
. ~/.bash_aliases
fi 
~~~~ 

Are above lines are missing in your ~/.bashrc file? Just append at the end of the ~/.bashrc, using a text editor such as vi/vim or joe. 
Examples
Let us create four aliases as follows: 
~~~~
$ vi ~/.bash_aliases 
~~~~
OR 
~~~~
$ joe ~/.bashrc 
~~~~
Append text: 

# update our debian/ubuntu box 

~~~~
alias update='sudo -- sh -c "apt update && apt upgrade"' 
~~~~
 
# make grep output colorful  
~~~~
alias grep='grep --color=auto' 
~~~~
 
# set eth0 as an interface for eth0   

~~~~
alias vnstat='vnstat -i eth0' 
~~~~
 
# flush redis cache for wp 
~~~~
alias flush_redis='redis-cli -h 127.0.0.1 FLUSHDB'
Save and close the file.
How to load aliases
All new aliases will be available next time you login using a new ssh/terminal session. To load changes immediately, type the following source command:
$ source ~/.bash_aliases
OR
$ . ~/.bash_aliases
How to list all of my aliases
To list all aliases, run:
$ alias
Sample outputs:
alias flush_redis='redis-cli -h 127.0.0.1 FLUSHDB'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias update='sudo -- sh -c "apt update && apt upgrade"'
alias vnstat='vnstat -i eth0'
How to use/call aliases
Just type alias name:
$ update
$ vnstat
$ flush_redis
~~~~



# DEBUGGING SHELL PROGRAMS
------------------------------------------------------------------------------


	• bash -n scriptname  # don't run commands; check for syntax errors only 
	
	• set -o noexec       # alternative (set option in script)

	• bash -v scriptname  # echo commands before running them 
	
	• set -o verbose      # alternative (set option in script)

	• bash -x scriptname  # echo commands after command-line processing 
	
	• set -o xtrace       # alternative (set option in script)

	• trap 'echo $varname' EXIT  # useful when you want to print out the values of variables at the point that your script exits

	• function errtrap {
	•   es=$?
	•   echo "ERROR line $1: Command exited with status $es."
	• }

	• trap 'errtrap $LINENO' ERR  # is run whenever a command in the surrounding script or function exits with non-zero status

	• function dbgtrap {
	•   echo "badvar is $badvar"
	• }

	• trap dbgtrap DEBUG  # causes the trap code to be executed before every statement in a function or script
	• # ...section of code in which the problem occurs...
	• trap - DEBUG  # turn off the DEBUG trap

	• function returntrap {
	•   echo "A return occurred"
	• }

	• trap returntrap RETURN  # is executed each time a shell function or a script executed with the . or source commands finishes executing 
	• ./


	• -a file                   # file exists or its compilation is successful 
	
	• -d file                   # file exists and is a directory 
	
	• -e file                   # file exists; same -a 
	
	• -f file                   # file exists and is a regular file (i.e., not a directory or other special type of file) 
	
	• -r file                   # you have read permission 
	
	• -s file                   # file exists and is not empty 
	
	• -w file                   # your have write permission 
	
	• -x file                   # you have execute permission on file, or directory search permission if it is a directory 
	
	• -N file                   # file was modified since it was last read 
	
	• -O file                   # you own file 
	
	• -G file                   # file's group ID matches yours (or one of yours, if you are in multiple groups) 
	
	• file1 -nt file2           # file1 is newer than file2 
	
    file1 -ot file2           # file1 is older than file2 


# For Loops 
~~~~
for x in {1..10}
do
  statements
done 

~~~~


~~~~
for name [in list]
do
  statements that can use $name
done
~~~~

~~~~
for (( initialisation ; ending condition ; update ))
do
  statements...
done
~~~~

# Functions 

The function refers to passed arguments by position (as if they were positional parameters), that is, $1, $2, and so forth.
$@ is equal to "$1" "$2"... "$N", where N is the number of positional parameters. $# holds the number of positional parameters.

~~~~
function functname() {
  shell commands
}
~~~~ 

Example: 
~~~~
!/bin/bash 

Basic function
print_something () {
  echo Hello I am a function
   }
  print_something
  print_something

~~~~

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php> 





	• unset -f functname  # deletes a function definition 
	
	• declare -f          # displays all defined functions in your login session


~~~~
#!/bin/bash
# Passing arguments to a function
print_something () {
echo Hello $1
}
print_something Mars
print_something Jupiter
~~~~
From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php> 

~~~~
#!/bin/bash
# Setting a return status for a function
print_something () {
echo Hello $1
return 5
}
print_something Mars
print_something Jupiter
echo The previous function has a return value of $?
~~~~

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php> 


~~~~
#!/bin/bash
# Experimenting with variable scope
var_change () {
local var1='local 1'
echo Inside function: var1 is $var1 : var2 is $var2
var1='changed again'
var2='2 changed again'
} 

var1='global 1'
var2='global 2' 

echo Before function call: var1 is $var1 : var2 is $var2 

var_change 

echo After function call: var1 is $var1 : var2 is $var2
~~~~

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php>  



# If Statement

~~~~
if condition
then
  statements
[elif condition
  then statements...]
[else
  statements]
fi 
~~~~
~~~~
#!/bin/bash
# else example
if [ $# -eq 1 ]
then
nl $1
else
nl /dev/stdin
fi
~~~~
From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

# or example
~~~~
#!/bin/bash
if [ $USER == 'bob' ] || [ $USER == 'andy' ]
then
ls -alh
else
ls
fi
~~~~
From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

# Basic if statement
~~~~
#!/bin/bash
if [ $1 -gt 100 ]
then
echo Hey that\'s a large number.
pwd
fi
date
~~~~ 

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

# elif statements
~~~~
#!/bin/bash
if [ $1 -ge 18 ]
then
echo You may go to the party.
elif [ $2 == 'yes' ]
then
echo You may go to the party but be back before midnight.
else
echo You may not go to the party.
fi
~~~~
From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

# Nested if statements
~~~~
#!/bin/bash
if [ $1 -gt 100 ]
then
echo Hey that\'s a large number.
if (( $1 % 2 == 0 ))
then
echo And is also an even number.
fi
fi
~~~~
From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

# and example
~~~~
#!/bin/bash
if [ -r $1 ] && [ -s $1 ]
then
echo This file is useful.
fi
~~~~ 

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php>  



# INPUT/OUTPUT REDIRECTORS




	• cmd1|cmd2  # pipe; takes standard output of cmd1 as standard input to cmd2 
	
	• < file     # takes standard input from file 
	
	• > file     # directs standard output to file 
	
	• >> file    # directs standard output to file; append to file if it already exists 
	
	• >|file     # forces standard output to file even if noclobber is set 
	
	• n>|file    # forces output to file from file descriptor n even if noclobber is set 
	
	• <> file    # uses file as both standard input and standard output 
	
	• n<>file    # uses file as both input and output for file descriptor n 
	
	• n>file     # directs file descriptor n to file 
	
	• n<file     # takes file descriptor n from file 
	
	• n>>file    # directs file description n to file; append to file if it already exists 
	
	• n>&        # duplicates standard output to file descriptor n 
	
	• n<&        # duplicates standard input from file descriptor n 
	
	• n>&m       # file descriptor n is made to be a copy of the output file descriptor 
	
	• n<&m       # file descriptor n is made to be a copy of the input file descriptor 
	
	• &>file     # directs standard output and standard error to file 
	
	• <&-        # closes the standard input 
	
	• >&-        # closes the standard output 
	
	• n>&-       # closes the ouput from file descriptor n 
	
	• n<&-       # closes the input from file descripor n 


# Operators




	• -lt                       # less than 
	
	• -le                       # less than or equal 
	
	• -eq                       # equal 
	
	• -ge                       # greater than or equal 
	
	• -gt                       # greater than 
	
	• -ne                       # not equal 

	• statement1 && statement2  # and operator 
	
	• statement1 || statement2  # or operator

	• -a               # and operator inside a test conditional expression
-o                     # or operator inside a test conditional expression 



# Process Handling


# To suspend a job, type CTRL+Z while it is running. You can also suspend a job with CTRL+Y.
# This is slightly different from CTRL+Z in that the process is only stopped when it attempts to read input from terminal.
# Of course, to interrupt a job, type CTRL+C.

	• myCommand &  # runs job in the background and prompts back the shell

	• jobs         # lists all jobs (use with -l to see associated PID)

	• fg           # brings a background job into the foreground
	• fg %+        # brings most recently invoked background job
	• fg %-        # brings second most recently invoked background job
	• fg %N        # brings job number N
	• fg %string   # brings job whose command begins with string
	• fg %?string  # brings job whose command contains string

	• kill -l               # returns a list of all signals on the system, by name and number
	• kill PID              # terminates process with specified PID
	• kill -s SIGKILL 4500  # sends a signal to force or terminate the process
	• kill -15 913          # Ending PID 913 process with signal 15 (TERM)
	• kill %1               # Where %1 is the number of job as read from 'jobs' command.

ps           # prints a line of information about the current running login shell and any processes running under it
ps -a        # selects all processes with a tty except session leaders

trap cmd sig1 sig2  # executes a command when a signal is received by the script
trap "" sig1 sig2   # ignores that signals
trap - sig1 sig2    # resets the action taken when the signal is received to the default

disown <PID|JID>    # removes the process from the list of jobs

wait                # waits until all background jobs have finished



# Strings



	• str1 == str2               # str1 matches str2 
	
	• str1 != str2               # str1 does not match str2 
	
	• str1 < str2                # str1 is less than str2 (alphabetically) 
	
	• str1 > str2                # str1 is greater than str2 (alphabetically) 
	
	• str1 \> str2               # str1 is sorted after str2 
	
	• str1 \< str2               # str1 is sorted before str2 
	
	• -n str1                    # str1 is not null (has length greater than 0) 
	
        * -z str1                    # str1 is null (has length 0) 

# Switchcase
~~~~

    case expression in
  pattern1 )
    statements ;;
  pattern2 )
    statements ;;
esac
~~~~ 


# case example
~~~~
#!/bin/bash

case $1 in
start)
echo starting
;;
stop)
echo stoping
;;
restart)
echo restarting
;;
*)
echo don\'t know
;;
esac
~~~~ 

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

~~~~
#!/bin/bash
 
space_free=$( df -h | awk '{ print $5 }' | sort -n | tail -n 1 | sed 's/%//' )
case $space_free in
[1-5]*)
echo Plenty of disk space available
;;
[6-7]*)
echo There could be a problem in the near future
;;
8*)
echo Maybe we should look at clearing out old files
;;
9*)
echo We could have a serious problem on our hands soon
;;
*)
echo Something is not quite right here
;;
esac
~~~~ 

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php>   



# Until
# ---------------------- 

~~~~
until condition; do
  statements
done
~~~~ 

# Basic until loop

~~~~
#!/bin/bash
counter=1
until [ $counter -gt 10 ]
do
echo $counter
((counter++))
done
echo All done
~~~~ 

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-loops.php#while>   



# Variables

~~~~ 

	• varname=value                # defines a variable 

	• varname=value command        # defines a variable to be in the environment of a particular subprocess 

	• echo $varname                # checks a variable's value 

	• echo $$                      # prints process ID of the current shell 

	• echo $!                      # prints process ID of the most recently invoked background job 

	• echo $?                      # displays the exit status of the last command 

	• read <varname>               # reads a string from the input and assigns it to a variable  

	• let <varname> = <equation>   # performs mathematical calculation using operators like +, -, *, /, % 

	• export VARNAME=value         # defines an environment variable (will be available in subprocesses)



   	• ${varname:-word}             # if varname exists and isn't null, return its value; otherwise return word 

	• ${varname:=word}             # if varname exists and isn't null, return its value; otherwise set it word and then return its value 

	• ${varname:?message}          # if varname exists and isn't null, return its value; otherwise print varname, followed by message and abort the current command or script 

	• ${varname:+word}             # if varname exists and isn't null, return word; otherwise return null 

	• ${varname:offset:length}     # performs substring expansion. It returns the substring of $varname starting at offset and up to length characters

	• ${variable#pattern}          # if the pattern matches the beginning of the variable's value, delete the shortest part that matches and return the rest 

	• ${variable##pattern}         # if the pattern matches the beginning of the variable's value, delete the longest part that matches and return the rest 

	• ${variable%pattern}          # if the pattern matches the end of the variable's value, delete the shortest part that matches and return the rest 

	• ${variable%%pattern}         # if the pattern matches the end of the variable's value, delete the longest part that matches and return the rest 

	• ${variable/pattern/string}   # the longest match to pattern in variable is replaced by string. Only the first match is replaced 

	• ${variable//pattern/string}  # the longest match to pattern in variable is replaced by string. All matches are replaced

	• ${#varname}                  # returns the length of the value of the variable as a character string


• *(patternlist)               # matches zero or more occurrences of the given patterns 

• +(patternlist)               # matches one or more occurrences of the given patterns 

• ?(patternlist)               # matches zero or one occurrence of the given patterns 

• @(patternlist)               # matches exactly one of the given patterns 

• !(patternlist)               # matches anything except one of the given patterns


	• $(UNIX command)              # command substitution: runs the command and returns standard output 

~~~~ 

# While
 

~~~~
while condition; do 

  statements 

done  
~~~~

# Basic while loop

~~~~ 
#!/bin/bash 

counter=1 

while [ $counter -le 10 ] 

do 

echo $counter 

((counter++)) 

done 

echo All done 
~~~~

# Whoami
 

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-loops.php#while>   

~~~~
if [[ `whoami` != root && `whoami` != obi ]]
then
   print "Script must be run as root or obi user."
   exit 1
fi
~~~~

# CLI




clear – Clear the terminal window 
~~~~
• clear
~~~~ 

 echo $? - Check if previous bash command run was successful 0 means yes and 1 means no 
 
 ~~~~  
 
 • echo $? 
 
 ~~~~

reset – Resets the terminal 
~~~~
• reset
~~~~ 

history – Lists all recent commands 
~~~~
• history

history | grep - Search for a specific command from the history 

• 3. Delete a line from the history with history -d line_number
• 4. If you want your commands not to remain in the history, run them
with a space before them after you will have set
HISTCONTROL=ignorespace 

• ! e.g. !357 -> re-runs command if entered into terminal
~~~~ 

xkill – Close a frozen window/application 
~~~~
• xkill
~~~~

Tab Completion 
~~~~
• Use TAB key for completion of characters on CLI 

• ctrl + u = Clear everything before the cursor 

• ctrl + a = To beginning of line 

• ctrl + e = To end of line 

• ctrl + b = Back one word 

• ctrl + f = Forward one word 

• ctrl + w = Cut last word 

• ctrl + k = Clear everything after the cursor 

• ctrl + _ = Undo
~~~~ 

Alter Screen Resolution 
~~~~
• xrandr --output --mode 1920x1200 
~~~~

Ctrl + r - Reverse search
~~~~ 
Type Ctrl+r to open the reverse search tool.
Search for any command from the history and press Ctrl+r again for
the previous one that contain the string you’re looking for. 
~~~~ 
General commands 
~~~~
• ./ - Runs file as executable 

• -- version – Checks version of installation 

• wget – Download file over internet 

• reboot – Restarts the system 

• Shutdown – shuts down server  

shutdown -r -> Shutdowns and reboots the node 

General commands continued…
• -- help – use to get information on command e.g. ls --help 
~~~~


# tmux
 


To install : yum install tmux

start new: 
~~~~
• tmux 
~~~~ 

start new with session name: 

~~~~
• tmux new -s myname   
~~~~
	
Attach: 

#tmux a  #  (or at, or attach) 

Attach to named:  

~~~~
• tmux a -t myname
~~~~ 

#list sessions: 
       ~~~~
	• tmux ls
       ~~~~
#kill session: 
~~~~
• tmux kill-session -t myname 
~~~~

Kill all the tmux sessions: 

~~~~
tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill 
~~~~
In tmux, hit the prefix ctrl+b (my modified prefix is ctrl+a) and then:

From <https://gist.github.com/MohamedAlaa/2961058> 



#4 pane window: 
~~~~
tmux new-window \; split-window -p 66 \; split-window -d \; split-window -h 
~~~~ 

The flow is: 
~~~~
	1. tmux new-window: create a window (ok, you wanted a new-session, that does create a window upon startup) 
	
	2. split-window -p 66: allocate bottom two thirds of the vertical space to a secondary pane and focus it 
	
	3. split-window -d: split bottom pane in half, vertically, without focusing the new pane (i.e. focus stays on second – now center – pane) 
	
	4. split-window -h: split center pane in half, horizontally 
~~~~

From <https://superuser.com/questions/1155771/tmux-split-into-4-panes> 


~~~~
:new<CR>  new session
s  list sessions
$  name session
~~~~
From <https://gist.github.com/MohamedAlaa/2961058> 
~~~~
Panes (splits)
%  vertical split
"  horizontal split
o  swap panes
q  show pane numbers
x  kill pane
+  break pane into window (e.g. to select text by mouse to copy)
-  restore pane from window
⍽  space - toggle between layouts
<prefix> q (Show pane numbers, when the numbers show up type the key to goto that pane)
<prefix> { (Move the current pane left)
<prefix> } (Move the current pane right)
<prefix> z toggle pane zoom

From <https://gist.github.com/MohamedAlaa/2961058> 
~~~~
~~~~
Windows (tabs)
c  create window
w  list windows
n  next window
p  previous window
f  find window
,  name window
&  kill window
~~~~
From <https://gist.github.com/MohamedAlaa/2961058> 

#Sync Panes 
	
You can do this by switching to the appropriate window, typing your Tmux prefix (commonly Ctrl-B or Ctrl-A) and then a colon to bring up a Tmux command line, and typing:  
	
~~~~	
:setw synchronize-panes 
~~~~ 
~~~~
You can optionally add on or off to specify which state you want; otherwise the option is simply toggled. This option is specific to one window, so it won’t change the way your other sessions or windows operate. When you’re done, toggle it off again by repeating the command. 

From <https://gist.github.com/MohamedAlaa/2961058> 

d  detach
t  big clock
?  list shortcuts
:  prompt
~~~~
From <https://gist.github.com/MohamedAlaa/2961058>   



# Crontab

~~~~
[Crontab schedule]
+---------------- minute (0 - 59)
|  +------------- hour (0 - 23)
|  |  +---------- day of month (1 - 31)
|  |  |  +------- month (1 - 12)
|  |  |  |  +---- day of week (0 - 6) (Sunday=0)
|  |  |  |  |
*  *  *  *  * command to be executed <script>
-- -- -- -- - --------------------------------- 
~~~~
crontab  -e  

crontab -l | grep <script_name> 


# Check Version

~~~~
cat /etc/oracle-release 
~~~~

# Diagnostics
 

RAM 
~~~~
	• free -th 
~~~~

RAM & CPU

~~~~
top 

top –c - Filtering 
~~~~ 
	
OS: 

~~~~	
hostnamectl
~~~~

SAR: 

Basic Output:
~~~~
sar   
~~~~
CPU Usage per Core: 
~~~~
sar -P ALL 
~~~~
Memory Usage: 
~~~~
sar -r   
~~~~
Swap Usage: 
~~~~
sar -S 
~~~~
 

From <https://www.gxd88.cn/sar>  

 
I/O: 
~~~~
sar -b 
~~~~

I/O by Block Device: 
~~~~
sar -d -p 
~~~~
 
Check Run queue and Load Average: 
~~~~
sar -q 
~~~~

Network Stats: 
~~~~
 sar -n DEV 
 

Where DEV can be one of the following 

DEV – Displays network devices vital statistics for eth0, eth1, etc., 

EDEV – Display network device failure statistics 

NFS – Displays NFS client activities 

NFSD – Displays NFS server activities 

SOCK – Displays sockets in use for IPv4 

IP – Displays IPv4 network traffic 

EIP – Displays IPv4 network errors 

ICMP – Displays ICMPv4 network traffic 

EICMP – Displays ICMPv4 network errors 

TCP – Displays TCPv4 network traffic 

ETCP – Displays TCPv4 network errors 

UDP – Displays UDPv4 network traffic 

SOCK6, IP6, EIP6, ICMP6, UDP6 are for IPv6 

ALL – This displays all of the above information. The output will be very long. 
~~~~ 

Historic Information: 
~~~~
 sar -f /var/log/sa/sa15 -n DEV 
~~~~ 

# Uptime: 

~~~~
 w 
~~~~


# Files & Directories


pwd command 

• pwd : prints current working directory 
~~~~	
Example: 
	
paul@debian8:~$ pwd 
	
/home/paul
~~~~ 

cd 

• cd -> changes your current directory + also return to your home dir
~~~~
Example: 
	
paul@debian8$ cd /etc 
	
paul@debian8$ pwd 
	
/etc
~~~~ 


cd – command continued 
~~~~
paul@debian8$ cd 
	
paul@debian8$ pwd 
	
/home/paul
~~~~ 

cd .. – Return to previous directory 
~~~~
paul@debian8$ pwd 
	
/usr/share/games 
	
paul@debian8$ cd .. 
	
paul@debian8$ pwd  
	
/usr/share
~~~~ 

Path Completion 

• The tab key can help you in typing a path without errors. Typing cd /et
followed by the tab key will expand the command line to cd /etc/.
When typing cd /Et followed by the tab key, nothing will happen
because you typed the wrong path (upper case E). 

• You will need fewer key strokes when using the tab key, and you will
be sure your typed path is correct!

ls – command 

• ls – lists contents of directory

~~~~
• Example:
stuff summer.txt
paul@debian8:~$ ls
allfiles.txt dmesg.txt services
paul@debian8:~
~~~~

ls –a - Shows all files including hidden ones 

~~~~
allfiles.txt .bash_profile dmesg.txt .lesshst stuff .. .bash_history
.bashrc services .ssh summer.txt
• Example:
• paul@debian8:~$ ls -a
paul@debian8:~$
~~~~ 

ls -hal 

• Shows all files with read and write permissions

~~~~
ls –ltr 
~~~~ 

ll – Lists contents of directory and gives date 
~~~~
obi@eze:~$ ll
total 189456
drwxr-xr-x 21 obi  obi       4096 Jan 25 18:30 ./
drwxr-xr-x  3 root root      4096 Jan 10 15:03 ../
-rw-r--r--  1 obi  obi        220 Jan 10 15:03 .bash_logout
-rw-r--r--  1 obi  obi       3771 Jan 10 15:03 .bashrc
drwx------ 15 obi  obi       4096 Jan 10 15:57 .cache/
-rwxr-xr-x  1 obi  obi         42 Jan 10 17:40 command_sub.sh*
-rwxr-xr-x  1 obi  obi         42 Jan 10 17:41 command_substitution.sh*
drwxr-xr-x 17 obi  obi       4096 Jan 10 18:28 .config/
~~~~

# Search for files in Directories 

~~~~
 ll <*STRING_TO_SEARCH*>
~~~~

# Working with files 

~~~~
file – determines file type of file
~~~~ 

~~~~
paul@laika:~$ file pic33.png
pic33.png: PNG image data, 3840 x 1200, 8-bit/color RGBA, noninterlaced
paul@laika:~$ file /etc/passwd
/etc/passwd: ASCII text
paul@laika:~$ file HelloWorld.c
HelloWorld.c: ASCII C program text
~~~~

# touch – creates empty files 

~~~~
paul@debian7:~$ ls -l total 0
paul@debian7:~$ touch file42
paul@debian7:~$ touch file33
paul@debian7:~$ ls –l
total 0
-rw-r--r-- 1 paul paul 0 Oct 15 08:57 file33
-rw-r--r-- 1 paul paul 0 Oct 15 08:56 file42
~~~~ 

# File Creation Commands
~~~~
vim
nano
cat
The Ctrl d key combination will send an EOF (End of File) to the running
process ending the cat command 
~~~~  



# File Compression 

~~~~ 

 gzip - 

# -f option : 

Sometimes a file cannot be compressed. Perhaps you are
trying to compress a file called “myfile1” but there is already a file called
“myfile1.gz”. In this instance, the “gzip” command won’t ordinarily work.

To force the “gzip” command to do its stuff simply use -f option: 

~~~~ 

~~~~ 

2.$ gzip -f myfile1.txt 

The above command would end up with a file called “mydoc.txt.gz” and
“mydoc.txt”. 

~~~~ 

~~~~

3.-L option : This option displays the gzip license. 

$ gzip -L filename.gz 


~~~~ 


~~~~

Unzip files

1) Extract a tar.gz archive 

The following command shell helps to extract tar files out a tar.gz archive.

tar -xvzf bigfile.tar.gz

x – Extract files
v – Verbose, print the file names as they are extracted one by one
z – The file is a “gzipped” file
f – Use the following tar archive for the operation!

~~~~ 


~~~~

2) Extract files to a specific directory or path 

We can extract the files into a specified directory by using the parameter “-C”.

tar -xvzf bigfile.tar.gz -C /folder/subfolder/
The tar command doesn’t create any files or folders.


~~~~ 


~~~~

Extract a single file 

To extract a single file out of an archive just add the file name after the command like this
tar -xz -f Music.tar.gz “./new/one.mp3”

To extract more than one file out of an archive
tar -xv -f Music.tar.gz “./new/two.mp3” “./new/three.mp3”

~~~~


~~~~

Use unzip command to unzip a zip file
The syntax is: 


unzip {file.zip} 

Use the following syntax if you want to extract/unzip to a particular destination directory: 


unzip -d /dest/directory/ {file.zip}


~~~~


# Check contents of File 
~~~~
cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
narad:x:500:500::/home/narad:/bin/bash 
~~~~ 

# Check difference between 2 files 
~~~~ 

diff filename1 filename2

~~~~

# rm – Deletes file forever 
~~~~
paul@debian7:~$ ls
BigBattle.txt file33 file42 SinkoDeMayo
paul@debian7:~$ rm BigBattle.txt
paul@debian7:~$ ls
file33 file42 SinkoDeMayo
paul@debian7:~
~~~~ 

# rm –i – Deleting file with a check 

~~~~ 
paul@debian7:~$ rm -i file33
rm: remove regular empty file `file33'? Yes 
~~~~  

# rm-f – Delete files 

~~~~ 
• VERY STRONG WAY TO DELETE FILES 

rm -f /* - Deletes all files in directory
~~~~  

# cp – Copy One file 

~~~~ 
paul@debian7:~$ ls
file42 SinkoDeMayo
paul@debian7:~$ cp file42 file42.copy
paul@debian7:~$ ls
file42 file42.copy SinkoDeMayo
~~~~ 

# Copy to another Directory 

~~~~ 
paul@debian7:~$ mkdir dir42
paul@debian7:~$ cp SinkoDeMayo dir42
paul@debian7:~$ ls dir42/
SinkoDeMay
~~~~  

# cp –r – Copy complete Directories 

~~~~ 
paul@debian7:~$ ls
dir42 file42 file42.copy SinkoDeMayo
paul@debian7:~$ cp -r dir42/ dir33
paul@debian7:~$ ls
dir33 dir42 file42 file42.copy SinkoDeMayo
paul@debian7:~$ ls dir33/
SinkoDeMayo
~~~~  

# copy multiple files to directory 
~~~~
paul@debian7:~$ cp file42 file42.copy SinkoDeMayo dir42/
paul@debian7:~$ ls
dir42/ file42 file42.copy SinkoDeMay
cp – i – To prevent overwriting of files
paul@debian7:~$ cp -i SinkoDeMayo file42
cp: overwrite `file42’? N
paul@debian7:~$
~~~~  

# More Copy notes 

~~~~ 
cp filename/directory - copy file and directory
cp filename directory/directory - copy and move file
cp filename directory/directory/filename.bak - creates backup file
~~~~  

# mv - Rename files with mv 
~~~~
paul@debian7:~$ mv file42 file33
paul@debian7:~$ ls
dir33 dir42 file33 file42.copy SinkoDeMayo
paul@debian7:~$
~~~~


# Running bash script 
~~~~
paul@debian7~$
./ - to run bash script
~~~~

# figlet 

~~~~
• sudo apt-get install figlet
~~~~ 

# mkdir – Makes new directory

# Creates Directory 

~~~~
paul@debian8:~/mydir$ mkdir otherstuff 
	
paul@debian8:~/mydir$ ls -l 
	
total 8 drwxr-xr-x 2 paul paul 4096 Sep 17 00:08 otherstuff 
	
drwxr-xr-x 2 paul paul 4096 Sep 17 00:08 stuff
~~~~ 

# mkdir –p – Creates Parent with new directory 

~~~~
paul@debian8:~$ mkdir -p mydir2/mysubdir2/threedirsdeep 
	
paul@debian8:~$ cd mydir2 
	
paul@debian8:~/mydir2$ ls -l 
	
total 4 drwxr-xr-x 3 paul paul 4096 Sep 17 00:11 mysubdir2 
	
paul@debian8:~/mydir2$ cd mysubdir2 
	
paul@debian8:~/mydir2/mysubdir2$
~~~~

# Search through Directory -  

~~~~
sudo du -a /dir/ | sort -n -r | head -n 20
~~~~

# rmdir – Deletes Directory 

~~~~
• paul@debian8:~/mydir$ rmdir otherstuff 
	
• paul@debian8:~/mydir$ cd ..  
~~~~
	
# rmdir –p – Deletes Directory 

~~~~	
• paul@debian8:~$ rmdir -p test42/subdir 
	
• @debian8:~
~~~~

# move file to another location 

~~~~
• mv directory directory - moves file to another location 
~~~~

# cat - Check contents of file 

~~~~
• cat /etc/hosts

• cat /etc/hosts | grep <string_your're_looking_for>  (To search for a value through a file)
~~~~	 

# Pattern searching 
~~~~
- grep -v pattern file.txt  
~~~~
Search for string and line number in file 
~~~~
- grep -inr 'string' filename/dir 
~~~~
#Find command 

Find Files Using Name in Current Directory 
~~~~
• Example:

• # find . -name tecmint.txt
• ./tecmint.txt

~~~~

# Find Files Under Home Directory 
~~~~
• Example:

• # find /home -name tecmint.txt
• /home/tecmint.txt!
~~~~


# Editing Files with Vi 

Vi Command Mode and Navigation

~~~~		
k  - Up one line.  
		
j -  Down one line.    
		
h  - Left one character.      
		
l  - Right one character.   
		
w  - Right one word. 
		
b  - Left one word. 
		
^  - Go to the beginning of the line. 
		
$  - Go to the end of the line.
~~~~

Vi Insert Mode 

~~~~		
i Insert at the cursor position. 
		
I Insert at the beginning of the line.  
		
a Append after the cursor position.  
		
A Append at the end of the line.
~~~~ 
		
Vi Line Mode 

~~~~
:w Writes (saves) the file.    
		
:w! Forces the file to be saved.  
		
:q Quit.   
		
:q! Quit without saving changes.  
		
:wq! Write and quit.  
		
:x Same as :wq. 
~~~~ 
		
Vi Line Mode 

~~~~
:n Positions the cursor at line n. 
		
:$ Positions the cursor on the last line. 
		
:set nu Turn on line numbering. 
		
:set nonu Turn off line numbering. 
		
:help [subcommand] Get help.
~~~~ 
		
Vi Modes 
~~~~
Mode Key 
		
Command Esc 
		
Insert i I a A 
~~~~ 
		
Line : 

Vi - Repeating Commands 

● Repeat a command by preceding it with a
number. 

~~~~	
○ 5k = Move up a line 5 times 
		
○ 80i = Insert 80 times 
		
○ 80i_ = Insert 80 "_" characters

Vi - Deleting Text 

~~~~	
x Delete a character. 
		
dw Delete a word. 
		
dd Delete a line.  
		
D Delete from the current position.
~~~~ 
		
Vi - Changing Text 
~~~~
r Replace the current character.  
		
cw Change the current word.       
		
cc Change the current line. 
		
c$ Change the text from the current position.  
		
C Same as c$.  
		
~ Reverses the case of a character.
~~~~ 
		
Vi - Copying and Pasting 

~~~~		
yy Yank (copy) the current line.  
		
y Yank the .   
		
p Paste the most recent deleted or yanked text.   
		
4yy - Pastes 4 lines down page 

~~~~ 
		
Vi - Undo / Redo  
		
~~~~
u Undo 
~~~~		
Ctrl-R Redo  
~~~~	 
		
Vi - Searching  
~~~~		
/ Start a forward search.  
		
? Start a reverse search.
~~~~ 

Vi - Recover swap file  
~~~~		
vim -r 
~~~~ 


Demo - vi 

~~~~
---TODO: Overlay with characters that I'm
using.---- (Might be hard, maybe come back and
do that later????)
key-mon --nomouse --scale=2.1
~~~~
Substitution Command 

~~~~
• :%s/NEW VALUE TO INPUT/g  
• :%s/NEW VALUE TO INPUT/gic
~~~~ 

Substitution Command II 

	• :s/first value at beginning of line/



Mass Delete and move to the bottom of file 

~~~~
• dG
~~~~ 

Move to the bottom of file

~~~~
	• ' o '                                             
~~~~

Move to the bottom of the file:  
					     
~~~~
Shift + g 
~~~~ 
					     
To reclaim previous command used 

~~~~				     
press shift key + ‘:’ and press the up arrow key 
~~~~				     

Set Numbering: 
~~~~
set nu 
~~~~
Check for tabs: 
~~~~
:set list - for yamls there should be no tabs or whitespaces between $ signs
~~~~ 

Remove tab checker: 

~~~~
:set nolist 
~~~~ 

Go to line: 

~~~~
:644 
~~~~


# Groups & Users


~~~~
groupadd group_name  

 

Example:  

 

groupadd friends  
~~~~

usermod
 
~~~~
usermod [ options ] username  

 

-c "COMMENT" 

-g GROUP 

Comments account. 

Specify the default group. 

-G GROUP1,GROUPN Additional groups. 

-s /shell/path Path to the user's shell. 
~~~~
 

Usermod  

~~~~
grep mysql /etc/passwd 
~~~~
 
~~~~ 
		
mysql:x:97:1003:MySQL Server: 

~~~~  

~~~~ 
/opt/mysql:/usr/sbin/nologin 
~~~~ 
 
~~~~ 
usermod -c "MySQL User" mysql 
~~~~  
~~~~ 		
grep mysql /etc/passwd 

mysql:x:97:1003:MySQL User: 
~~~~  
~~~~ 		
/opt/mysql:/usr/sbin/nologin 

~~~~ 

~~~~
/etc/group 

root:x:0: 

sales:x:1001:john,mary 

The format of the /etc/group file: 

group_name:password:GID:account1,accountN 
~~~~
 
~~~~
groups [username] 

groups root 

 

root 

~~~~ 

groupadd [ options ]group_name 

~~~~
groupadd web 

tail -1 /etc/group 

web:x:1003: 

groupadd -g 2500 db 

tail -1 /etc/group 

db:x:2500: 

~~~~ 

 

Groupmod  

 
~~~~
groupmod [options] group_name 

-g GID 

-n GROUP 

Change the group ID to GID. 
~~~~ 

# Rename the group to GROUP. 

 
~~~~
groupmod 
~~~~
 
~~~~
grep web /etc/group 

web:x:1003: 
~~~~
 
~~~~
groupmod -g 1234 web 

grep web /etc/group 

web:x:1234: 
~~~~
 
~~~~
groupmod -n http web 

grep http /etc/group 

http:x:1234:  
~~~~ 

#Group Deletion  

 
~~~~
groupdel <group_name> 

groupdel db  
~~~~

cat and grep file for particular expression: 

cat /etc/group | grep <part_group_name>  

# Troubleshooting User accounts: 

#The issue was the client didn't have access to the BE of the Prod domain so they couldn't use winscp to login 

 

# Create BE and check if they can login  

If they can't, try and login into their account from another Linux box  e.g. ssh <theiruserid>@<targetserver>   

If you can login, then check their if their user permissions are correct via lslogins <username> compare the results to their other BE accounts in other domains  

Check if the client can telnet to port 22 on the server (This rules out any network issues on their side)  

# Create new user with Useradd  

 

useradd[options] username  

 

-c "COMMENT" 

-m 

-s /shell/path 

Comments for the account. 

Create the home directory. 

The path to the user's shell. 

 

#Useradd  

 
~~~~
useradd –c "Grant Stewart" –m –s /bin/bash grant 
~~~~
 

Note:This is one command line. It's displayed on 

multiple lines for readability. 

 
~~~~
useradd –c "Grant Stewart" –m –s /bin/bash grant 
~~~~
 

#SECONDARY USER ACCOUNT Creation:  

 
~~~~
adduser jbloggs <Create user> 
~~~~
 
~~~~
passwd jbloggs  <Set Password> 
~~~~
 
~~~~
chage -d 0 jbloggs  Triggers user to change it when they log in 
~~~~
 
~~~~
chage -E 6 jbloggs - 6 month expiry date 
~~~~
 
~~~~
id cpearson 
~~~~
 
~~~~
usermod -a -G <group_name> jbloggs - add to group  
~~~~ 

#Create a password using passwd  

 
~~~~
passwd grant 

 

Enter new UNIX password: 

Retype new UNIX password: 

passwd: password updated 

successfully 
~~~~
 
~~~~
tail -1 /etc/passwd 

 

grant:x:1000:1000:Grant Stewart:/home/grant 

:/bin/bash 

~~~~ 

~~~~
tail -1 /etc/shadow 
	
grant:66iDDsgsPYtR8c2Uc.:16507:0:99999:7::: 
~~~~ 
	
Account information for "grant" 

 

More useradd options  

~~~~

-g GROUP Specify the default group. 

-G GROUP1,GROUPN Additional groups. 
~~~~
 
~~~~
useradd –c "Eddie Harris" –m –s 
~~~~
 
~~~~
/bin/bash –g sales –G projectx 

eharris 
~~~~
 
~~~~
useradd 

passwd eharris 

 

Enter new UNIX password: 

Retype new UNIX password: 

passwd: password updated successfully 
~~~~
 

System or ApplicationAccounts 

~~~~
useradd –c "Apache Web Server 
~~~~
 
~~~~
User" –d /opt/apache –r –s 

/usr/sbin/nologin apache 
~~~~
 
~~~~
tail -1 /etc/passwd 
~~~~
 
~~~~
apache:x:999:999:Apache Web Server 

User:/opt/apache:/usr/sbin/nologin 
~~~~
 
~~~~
/etc/skel 

 

● When using -m the home directory for the 

account is created. 

● The contents of /etc/skel are copied into the 

home directory. 

● /etc/skel typically contains shell configuration 

files. (.profile, .bashrc,etc) 
~~~~
 

More user adoptions II 

 
~~~~
-r Create a system account. 

-d /home/dir Specify the home directory. 
~~~~
 
~~~~
Use -u to specify the UID 
useradd –c "MySQL Server" –d  
~~~~

 
~~~~
/opt/mysql -u 97 –s /usr/sbin/nologin 

mysql 
~~~~
 
~~~~
tail -1 /etc/passwd 

 

mysql:x:97:1003:MySQL Server: 

/opt/mysql:/usr/sbin/nologin  
~~~~

# Delete user account:  

 

 
~~~~ 
	
userdel [-r]username 

ls /home 

 

eharris grant 

 

userdel eharris 

 

ls /home 

 

eharris grant 

 

userdel -r grant 

 

ls /home 

 

eharris  

lslogins <user_account_name>  
~~~~
 
~~~~
$ id 
 
uid=503(tclark) gid=506(authors) 
groups=504(tclark),506(authors)  
~~~~ 
	
# Logging into new group 

~~~~
$ id 
 
uid=503(tclark) gid=504(tclark) 
groups=504(tclark),506(authors) 
~~~~  
	
~~~~	
$ newgrp authors 
~~~~  
	
~~~~
$ id 
 
uid=503(tclark) gid=506(authors) 
groups=504(tclark),506(authors)  
~~~~

# Networks


#Change Hostname: 
~~~~ 
	
hostnamectl set-hostname 'host_name' 

 

hostnamectl set-hostname 'node01'  
~~~~

# Checking Open files  

 

• lsof 

 
~~~~
• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• init 1 root cwd DIR 253,0 4096 2 / 

• init 1 root rtd DIR 253,0 4096 2 / 

• init 1 root txt REG 253,0 145180 147164 /sbin/init 

• init 1 root mem REG 253,0 1889704 190149 /lib/libc-2.12.so 

• init 1 root 0u CHR 1,3 0t0 3764 /dev/null 

• init 1 root 1u CHR 1,3 0t0 3764 /dev/null 

• init 1 root 2u CHR 1,3 0t0 3764 /dev/null 

• init 1 root 3r FIFO 0,8 0t0 8449 pipe 

• init 1 root 4w FIFO 0,8 0t0 8449 pipe 

• init 1 root 5r DIR 0,10 0 1 inotify 

• init 1 root 6r DIR 0,10 0 1 inotify 

• init 1 root 7u unix 0xc1513880 0t0 8450 socket 
~~~~
 

# List User Specific Open Files  

 
~~~~
• lsof -u cyberpunk 

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• sshd 1838 cyberpunk cwd DIR 253,0 4096 2 / 

• sshd 1838 cyberpunk rtd DIR 253,0 4096 2 / 

• sshd 1838 cyberpunk txt REG 253,0 532336 188129 /usr/sbin/sshd 

• sshd 1838 cyberpunk mem REG 253,0 19784 190237 /lib/libdl-2.12.so 

• sshd 1838 cyberpunk mem REG 253,0 122436 190247 /lib/libselinux.so.1 

• sshd 1838 cyberpunk mem REG 253,0 255968 190256 

/lib/libgssapi_krb5.so.2.2 

• sshd 1838 cyberpunk mem REG 253,0 874580 190255 /lib/libkrb5.so.3.3 

 ~~~~

Find Processes running on Specific Port 

~~~~
• # lsof -i TCP:22 

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• sshd 1471 root 3u IPv4 12683 0t0 TCP *:ssh (LISTEN) 

• sshd 1471 root 4u IPv6 12685 0t0 TCP *:ssh (LISTEN) 
~~~~
 

#List Only IPv4 & IPv6 Open Files  

 ~~~~

• # lsof -i 4 

 
• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• rpcbind 1203 rpc 6u IPv4 11326 0t0 UDP *:sunrpc 

• rpcbind 1203 rpc 7u IPv4 11330 0t0 UDP *:954 

• rpcbind 1203 rpc 8u IPv4 11331 0t0 TCP *:sunrpc (LISTEN) 

• avahi-dae 1241 avahi 13u IPv4 11579 0t0 UDP *:mdns 

• avahi-dae 1241 avahi 14u IPv4 11580 0t0 UDP *:58600 

~~~~	
 
~~~~ 
	
• # lsof -i 6 

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• rpcbind 1203 rpc 9u IPv6 11333 0t0 UDP *:sunrpc 

• rpcbind 1203 rpc 10u IPv6 11335 0t0 UDP *:954 

• rpcbind 1203 rpc 11u IPv6 11336 0t0 TCP *:sunrpc (LISTEN) 

• rpc.statd 1277 rpcuser 10u IPv6 11858 0t0 UDP *:55800 

• rpc.statd 1277 rpcuser 11u IPv6 11862 0t0 TCP *:56428 (LISTEN) 

• cupsd 1346 root 6u IPv6 12112 0t0 TCP localhost:ipp (LISTEN) 

 ~~~~

#List Open Files of TCP Port ranges 1-1024  

 
~~~~ 
	
lsof -i TCP:1-1024  

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• rpcbind 1203 rpc 11u IPv6 11336 0t0 TCP *:sunrpc (LISTEN) 

• cupsd 1346 root 7u IPv4 12113 0t0 TCP localhost:ipp (LISTEN) 

• sshd 1471 root 4u IPv6 12685 0t0 TCP *:ssh (LISTEN) 

• master 1551 root 13u IPv6 12898 0t0 TCP localhost:smtp (LISTEN) 

• sshd 1834 root 3r IPv4 15101 0t0 TCP 192.168.0.2:ssh->192.168.0.1:conclave-cpp (ESTABLISHED) 

• sshd 1838 cyberpunk 3u IPv4 15101 0t0 TCP 192.168.0.2:ssh->192.168.0.1:conclave-cpp 

(ESTABLISHED) 

• sshd 1871 root 3r IPv4 15842 0t0 TCP 192.168.0.2:ssh->192.168.0.1:groove (ESTABLISHED) 

• httpd 1918 root 5u IPv6 15991 0t0 TCP *:http (LISTEN) 

• httpd 1918 root 7u IPv6 15995 0t0 TCP *:https (LISTEN) 
~~~~
 

# Exclude User with ‘^’ Character  

 
~~~~
• lsof -i -u^root  

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• rpcbind 1203 rpc 6u IPv4 11326 0t0 UDP *:sunrpc 

• rpcbind 1203 rpc 7u IPv4 11330 0t0 UDP *:954 

• rpcbind 1203 rpc 8u IPv4 11331 0t0 TCP *:sunrpc (LISTEN) 

• rpcbind 1203 rpc 9u IPv6 11333 0t0 UDP *:sunrpc 

• rpcbind 1203 rpc 10u IPv6 11335 0t0 UDP *:954 

• rpcbind 1203 rpc 11u IPv6 11336 0t0 TCP *:sunrpc (LISTEN) 

• avahi-dae 1241 avahi 13u IPv4 11579 0t0 UDP *:mdns 

• avahi-dae 1241 avahi 14u IPv4 11580 0t0 UDP *:58600 

• rpc.statd 1277 rpcuser 5r IPv4 11836 0t0 UDP *:soap-beep 

• rpc.statd 1277 rpcuser 8u IPv4 11850 0t0 UDP *:55146 

• rpc.statd 1277 rpcuser 9u IPv4 11854 0t0 TCP *:32981 (LISTEN) 

• rpc.statd 1277 rpcuser 10u IPv6 11858 0t0 UDP *:55800 

• rpc.statd 1277 rpcuser 11u IPv6 11862 0t0 TCP *:56428 (LISTEN) 

~~~~ 

# Find Out who’s Looking What Files and Commands?  

~~~~ 

• lsof -i –u 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• bash 1839 cyberpunk cwd DIR 253,0 12288 15 /etc 

• ping 2525 cyberpunk cwd DIR 253,0 12288 15 /etc 

~~~~	
 

#List all Network Connections  

~~~~ 

• lsof -i 

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• rpcbind 1203 rpc 6u IPv4 11326 0t0 UDP *:sunrpc 

• rpcbind 1203 rpc 7u IPv4 11330 0t0 UDP *:954 

~~~~ 

#Search by PID  

 
~~~~
• # lsof -p 1  

 

• COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME 

• init 1 root cwd DIR 253,0 4096 2 / 

• init 1 root rtd DIR 253,0 4096 2 / 

• init 1 root txt REG 253,0 145180 147164 /sbin/init 

• init 1 root mem REG 253,0 1889704 190149 /lib/libc-2.12.so 

• init 1 root mem REG 253,0 142472 189970 /lib/ld-2.12.so 
~~~~
 

#Kill all Activity of Particular User  

 
~~~~
• # kill -9 `lsof -t -u  

~~~~ 
	
Network Interfaces: 

Bring Interface up / down  

 

 

#Bring Interface up  

~~~~

ifup eth0  

~~~~ 

#Bring Interface down  

~~~~ 

ifdown eth0  

~~~~ 

Network Interface  

 

#Check network interfaces: 

 
~~~~
ip addr  

Monitor: 

root@server1 ~]# ip addr show  

 

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 

 group default qlen 1000 

 link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 

 inet 127.0.0.1/8 scope host lo 

 valid_lft forever preferred_lft forever 

 inet6 ::1/128 scope host  

 valid_lft forever preferred_lft forever 

2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel 

 state UP group default qlen 1000 

 link/ether 00:0c:29:50:9e:c9 brd ff:ff:ff:ff:ff:ff 

 inet 192.168.4.210/24 brd 192.168.4.255 scope global dynamic 

 noprefixroute ens33 

 valid_lft 1370sec preferred_lft 1370sec 

 inet6 fe80::959:3b1a:9607:8928/64 scope link noprefixroute  

 valid_lft forever preferred_lft forever  

  List out all connections  

 ~~~~

#The first and most simple command is to list out all the current connections. 

 
~~~~
$ netstat -a  

 

Active Internet connections (servers and established) 

Proto Recv-Q Send-Q Local Address Foreign Address State 

tcp 0 0 enlightened:domain : LISTEN 

tcp 0 0 localhost:ipp : LISTEN 

tcp 0 0 enlightened.local:54750 li240-5.members.li:http ESTABLISHED 

tcp 0 0 enlightened.local:49980 del01s07-in-f14.1:https ESTABLISHED 

tcp6 0 0 ip6-localhost:ipp [::]:* LISTEN 

~~~~

#List only TCP or UDP connections 

• $ 

 
~~~~
netstat -at 

 

Active Internet connections (servers and established) 

Proto Recv-Q Send-Q Local Address Foreign Address State 

tcp 0 0 enlightened:domain : LISTEN 

tcp 0 0 localhost:ipp : LISTEN 

tcp 0 0 enlightened.local:36310 del01s07-in-f24.1:https 

ESTABLISHED 

tcp 0 0 enlightened.local:45038 a96-17-181-10.depl:http 

ESTABLISHED 

 ~~~~

#List udp connections only  

 
~~~~
$ netstat -au  

 

Active Internet connections (servers and established) 

Proto Recv-Q Send-Q Local Address Foreign Address State 

udp 0 0 *:34660 : 

udp 0 0 enlightened:domain : 

udp 0 0 *:bootpc : 

udp 0 0 enlightened.local:ntp : 

udp 0 0 localhost:ntp : 

udp 0 0 *:ntp : 

 ~~~~

#Disable reverse dns lookup for faster output  

 
~~~~
 $ netstat -ant  

 

Active Internet connections (servers and established) 

Proto Recv-Q Send-Q Local Address Foreign Address State 

tcp 0 0 127.0.1.1:53 0.0.0.0:* LISTEN 

tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 

tcp 0 0 192.168.1.2:49058 173.255.230.5:80 ESTABLISHED 

tcp 0 0 192.168.1.2:33324 173.194.36.117:443 ESTABLISHED 

tcp6 0 0 ::1:631 :::* LISTEN 
~~~~
 

#List out only listening connections  

 
~~~~
• $ netstat -tnl 

 

Active Internet connections (only servers) 

Proto Recv-Q Send-Q Local Address Foreign Address State 

tcp 0 0 127.0.1.1:53 0.0.0.0:* LISTEN 

tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 

ffctcp6 0 0 ::1:631 :::* LISTEN 
~~~~
 

# netstat -tulpn  

~~~~ 

• netstat -tulpn is merge between tcp and udp 

 

#Get process name/pid and user id  

 

sudo netstat -nlpt 



• Active Internet connections (only servers) 

• Proto Recv-Q Send-Q Local Address Foreign Address State 

PID/Program name 

• tcp 0 0 127.0.1.1:53 0.0.0.0:* LISTEN 

1144/dnsmasq 

• tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 

661/cupsd 

• tcp6 0 0 ::1:631 :::* LISTEN 661/cupsd 

e option along with the p option to get the 

username too. 
~~~~ 
	
#sudo netstat -ltpe 
~~~~
• Active Internet connections (only servers) 

• Proto Recv-Q Send-Q Local Address Foreign Address State 

User Inode PID/Program name 

• tcp 0 0 enlightened:domain : LISTEN root 

11090 1144/dnsmasq 

• tcp 0 0 localhost:ipp : LISTEN root 9755 

661/cupsd 

• tcp6 0 0 ip6-localhost:ipp [::]:* LISTEN root 9754 

661/cupsd 
~~~~
 

#Print statistics 

 
~~~~
• $ netstat -s 



Ip: 

32797 total packets received 

0 forwarded 

0 incoming packets discarded 

32795 incoming packets delivered 

29115 requests sent out 

60 outgoing packets dropped 

~~~~ 

#Display kernel routing information 

~~~~

• $ netstat -rn  

 

• Kernel IP routing table 

• Destination Gateway Genmask Flags MSS Window irtt 

Iface 

• 0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0 

• 192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0 

~~~~ 

#Print network interfaces 

 
~~~~
• $ netstat -ie  

 

Kernel Interface table 

eth0 Link encap:Ethernet HWaddr 00:16:36:f8:b2:64 

inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0 

inet6 addr: fe80::216:36ff:fef8:b264/64 Scope:Link 

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 

RX packets:31682 errors:0 dropped:0 overruns:0 frame:0 

TX packets:27573 errors:0 dropped:0 overruns:0 carrier:0 

collisions:0 txqueuelen:1000 

RX bytes:29637117 (29.6 MB) TX bytes:4590583 (4.5 MB) 

 Interrupt:18 Memory:da000000-da020000  
~~~~
 

#Display multicast group information 

 
~~~~
netstat -g  

 

Check if a service is running 

 [ansibleadm@uk-lon-lofm08 ~]$ netstat -tupn  

 

(Not all processes could be identified, non-owned process info 

will not be shown, you would have to be root to see it all.) 

Active Internet connections (w/o servers) 

Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program 

name 

tcp 0 0 10.61.223.188:43192 10.61.239.11:1984 TIME_WAIT - 

tcp 0 0 10.61.223.188:43194 10.61.239.11:1984 TIME_WAIT - 

tcp 0 0 10.61.223.188:43190 10.61.239.11:1984 TIME_WAIT - 

tcp 0 0 10.61.223.188:43193 10.61.239.93:1984 TIME_WAIT - 

tcp 0 0 10.61.223.188:43191 10.61.239.93:1984 TIME_WAIT - 

tcp 0 0 10.61.223.188:22 10.14.40.60:54034 ESTABLISHED -       

~~~~

# Netstat with grep  

 
~~~~
netstat -nap |grep :3506  
~~~~

#Testing Connectivity with Ping  

 

Network Troubleshooting:

Format: 

 

ping HOST 

ping -c COUNT HOST 

 
~~~~
Example: 

ping -c 3 google.com 

 

$ ping -c 3 google.com 

 

PING google.com (216.58.2.7) 56 bytes of data. 

64 bytes from 216.58.2.7: icmp_seq=1 ttl=53 time=20.1 ms 

64 bytes from 216.58.2.7: icmp_seq=2 ttl=53 time=20.2 ms 

64 bytes from 216.58.2.7: icmp_seq=3 ttl=53 time=23.9 ms 

--- google.com ping statistics --- 

3 packets transmitted, 3 received, 0% packet loss, time 

2004ms 

rtt min/avg/max/mdev = 21.489/22.924/24.154/1.111 ms 
~~~~
 
~~~~
$ ping -c 3 google.com  

 

PING google.com (216.58.2.7) 56 bytes of data. 

From 216.58.2.7 icmp_seq=1 Destination Host Unreachable 

From 216.58.2.7 icmp_seq=2 Destination Host Unreachable 

From 216.58.2.7 icmp_seq=3 Destination Host Unreachable 

--- google.com ping statistics --- 

3 packets transmitted, 0 received, +3 errors, 100% packet 

loss, time 2002ms 

pipe 3 
~~~~
 
~~~~
$ ping -c 3 10.0.2.2  

 

PING 10.0.2.2 (10.0.2.2) 56(84) bytes of data. 

64 bytes from 10.0.2.2: icmp_seq=1 ttl=63 time=0.272 ms 

64 bytes from 10.0.2.2: icmp_seq=2 ttl=63 time=0.103 ms 

64 bytes from 10.0.2.2: icmp_seq=3 ttl=63 time=0.202 ms 

--- 10.0.2.2 ping statistics --- 

3 packets transmitted, 3 received, 0% packet loss, time 

2001ms 

rtt min/avg/max/mdev = 0.103/0.192/0.272/0.070 ms 
~~~~ 

# Traceroute  

 
~~~~
traceroute -n google.com 

 

traceroute to google.com (216.58.2.7), 30 hops 

max, 60 byte packets 

Diagnosing Network Connections 413 

1 10.0.2.2 0.296 ms 0.178 ms 0.220 ms 

2 192.168.1.1 2.529 ms 2.713 ms 2.630 ms 

3 72.14.237.231 23.750 ms 22.087 ms 

12.122.132.137 22.701 ms 

4 216.58.216.78 20.549 ms 12.250.16.30 22.904 

ms 216.58.216.78 20.724 ms 
~~~~

~~~~
$ tracepath -n google.com 

1?: [LOCALHOST] pmtu 1500 

1: 10.0.2.2 0.470ms 

1: 10.0.2.2 0.649ms 

2: 192.168.1.1 2.147ms asymm 64 
~~~~
... 

# Using curl to check firewall connectivity   
	
~~~~ 
curl -k https://<url>:<port.no>
~~~~

# Download files with wget 
	
~~~~ 
wget --no-check-certificate	
~~~~
	
# Netstat  

 

The netstat Command 

 
~~~~
-n Display numerical addresses and ports. 

-i Displays a list of network interfaces. 

-r Displays the route table. (netstat -rn) 

-p Display the PID and program used. 

-l Display listening sockets. (netstat -nlp) 

-t Limit the output to TCP (netstat -ntlp) 

-u Limit the output to UDP (netstat -nulp) 
~~~~
 
~~~~
[jason@linuxsvr ~]$ netstat -i 

 

Kernel Interface table 

Iface MTU RX-OK RX-ERR RX-DRP RX-OVR TX-OK TX-ERR TX-DRP TX-OVR Flg 

eth0 1500 3975 0 0 0 2627 0 0 0 BMRU 

lo 65536 8 0 0 0 8 0 0 0 LRU 
~~~~
 
~~~~
[jason@linuxsvr ~]$ netstat -rn  

 

Kernel IP routing table 

Destination Gateway Genmask Flags MSS Window irtt Iface 

0.0.0.0 10.0.2.2 0.0.0.0 UG 0 0 0 eth0 

10.0.2.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0 
~~~~
 
~~~~
[jason@linuxsvr ~]$ sudo netstat -ntlp  

 

Active Internet connections (only servers) 

Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program 

name 

tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN 943/sshd 

tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 1313/master 
~~~~
 

#Telnet  

 
~~~~
telnet HOST_OR_IP PORT_NUMBER 

$ telnet google.com 80 

Trying 216.58.2.7... 

Connected to google.com. 

Escape character is '^]'. 

GET / 

HTTP/1.0 200 OK 

^] 

telnet> quit 

closed. 
~~~~

~~~~ 

[root@server1 ~]# nmcli con show  

 

NAME UUID TYPE DEVICE  

ens33 db6f53bd-654e-45dd-97ef-224514f8050a ethernet ens33  

Connection Properties

[root@server1 ~]# nmcli con show ens33 

connection.id: ens33 

connection.uuid: db6f53bd-654e-45dd-97ef- 

 224514f8050a 

connection.stable-id: -- 

connection.type: 802-3-ethernet 

connection.interface-name: ens33 

connection.autoconnect: yes 

connection.autoconnect-priority: 0 

connection.autoconnect-retries: -1 (default) 

connection.multi-connect: 0 (default) 

connection.auth-retries: -1 

connection.timestamp: 1558778720 

connection.read-only: no 

connection.permissions: -- 

connection.zone: -- 

connection.master: -- 

connection.slave-type: -- 

connection.autoconnect-slaves: -1 (default)  
~~~~

	
Configure eth0 interface with ipv6 and DNS 

~~~~	
• Already existing IPv4 network configurations should not be impacted.  

 

Command Action/Description  

 

Configuring ipv6 on ethernet interface - nmcli connection modify system ipv6.addresses 2020::1/64  

ipv6.dns 2020::2 ipv6.method manual 

 

To restart/activate connection - nmcli connection up system   

 

To display IP Address configurations - ip address show   

 

To display connection information - nmcli connection show system   

 

To verify configured DNS IP address - more /etc/resolv.conf  

 

To display Manual page for nmcli - man nmcli  

 

To display Manual page for nmcli-examples - man nmcli-examples   

~~~~

#Configure Static Route: 

Configure static route on system.example.com for destination 10.1.1.0/24 via 192.168.99.30.  

 
~~~~
• Route configuration must be persistent after reboot. 

• eth0 should be used as exit interface.  

 

#Command Action/Description  

 

Adding static route in runtime - ip route add 10.1.1.0/24 via 192.168.99.30   

 

To display route(s) - ip route show or route -n   

 

To add persistent route using command line - nmcli connection modify system ipv4.routes “10.1.1.0/24 192.168.99.30”  

 

To add persistent route using config file  

 

vim /etc/sysconfig/network-scripts/route-system  

 

10.1.1.0/24 via 192.168.99.30 dev eth0  

 

:wq  
~~~~
 
#Configure hostname resolution: 


• Set the hosts file as priority for hostname resolution in nsswitch.conf file.  

• Test if hostname resolution is working fine.   

 

~~~~ 

#Command Action/Description   

 

To add entry in hosts file  

 

vim /etc/hosts 

192.168.99.20 system1.example.com  

:wq 

 

To verify hostname resolution is working fine - getent hosts system1.example.com  
 

To restart/activate connection - nmcli connection up system   


Note : 

Remove ssh service from services list ,if you don’t remove ssh service ,then rich rule configured to accept ssh traffic from 192.168.99.0/24 

network only will not be effective. This is due to order in which firewalld evaluates the different definitions on firewall. If firewalld will find 

ssh service on services list, it will allow access irrespective of accessing network and rich rule will be ignored. 

 

To Test This :  

We have only one network, so it is not possible to test this. To test this working of rule , you just add this rule to allow access for some host  

not on 192.168.99.0/24 network and then test ssh connection from ipaserver.example.com, it must be denied. 

 
~~~~

Command Action/Description  

 
~~~~ 

Displaying firewall configurations - firewall-cmd --list-all   

 

Adding firewalld rich rule to accept traffic form 192.168.99.0/24 network - firewall-cmd --add-rich-rule ‘rule family=“ipv4” source address=“192.168.99.0/24” service name=“ssh” accept’ --permanent 

 

Removing ssh service from services list - firewall-cmd --remove-service=ssh --permanent   

 

Reloading firewall to make changes effective - firewall-cmd --reload  

 

To verify firewall configs after making changes - firewall-cmd --list-all  
~~~~
	
Packet Capture: 

~~~~
tcpdump 

 

-n Display numerical addresses and ports. 

-A Display ASCII (text) output. 

-v Verbose mode. Produce more output. 

-vvv Even more verbose output. 
~~~~
 

$ sudo tcpdump  

 
~~~~
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode 

listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes 

19:25:49.639495 IP linuxsvr.ssh > 10.0.2.2.64440: Flags [P.], seq 3312803324:3312803408, ack 

2443835, win 40880, length 84 

19:25:49.639586 IP linuxsvr.ssh > 10.0.2.2.64440: Flags [P.], seq 84:120, ack 1, win 40880, length 36 

19:25:49.639750 IP 10.0.2.2.64440 > linuxsvr.ssh: Flags [.], ack 84, win 65535, length 0 

19:25:49.639763 IP 10.0.2.2.64440 > linuxsvr.ssh: Flags [.], ack 120, win 65535, length 0  
~~~~
 
~~~~
$ sudo tcpdump –Anvvv  

 

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes 

19:44:27.067530 IP (tos 0x10, ttl 64, id 5120, offset 0, flags [DF], proto TCP (6), length 64) 

10.0.2.44.37534 > 10.0.2.15.80: Flags [P.], cksum 0xfe34 (incorrect -> 0xce40), seq 1:13, ack 1, win 

683, options [nop,nop,TS val 1585227 ecr 1584441], length 12 

E..@..@.@.(............P..>.:........4..... 

..0K..-9GET /about 
~~~~
 

 

 
~~~~
tcpdump -w /temp/traffic.pcap -i eno1 -v host 9.9.9.9  
~~~~
 

~~~~
tcpdump -w /<dir>/traffic.pcap -i <interface> -v host <ip_addr_interface_is_sending_traffic_to> 
~~~~
	
	
# Package Management
 

Update & Upgrade OS packages 
~~~~
	• sudo apt-get update

	• sudo apt-get upgrade
~~~~
Install package
~~~~
	• sudo apt-get install 
~~~~
Uninstall packages 
~~~~
	• sudo apt-get remove --purge

	• sudo apt-get remove
~~~~
# CENTOS/REDHAT COMMANDS 
~~~~
Install package 

	• yum install httpd
~~~~
Uninstall package 
~~~~
	• yum remove package_name
~~~~
Update/Upgrade packages 
~~~~
	• yum update

	• yum upgrade

	• yum update -y 
~~~~
Get Details  
~~~~
	• rpm -qi <package_name> 
	• yum info <package_name>  
~~~~


# Process Management



~~~~
Run CPU intensive process on System with nice value of -5 to give more CPU attention than default.  
 

• Adjust the niceness value to 5 so that CPU pays less attention to this process  

 

Note : nice value can be between -20 to 19. Lesser the NICE value, more CPU resources will be used. Higher the nice value, less  

CPU attention will be given.  

 

Never run process with nice value of -20 ,CPU will give highest priority and no other jobs will be able to run. 
~~~~
 

Command Action/Description  

 
~~~~
To start process with nice value -5 - nice -n -5 dd if=/dev/zero of=/dev/null   

 

To adjust nice value                - renice -n 5 -p PID               

 

To verify changes                   - top   
~~~~

Run below command in back ground with nice value of 10. 

 
~~~~
sleep 3600 
~~~~
 

Command Action/Description  

 
~~~~
To start a process with pre-defined nice value -  nice -n 10 sleep 3600 &   
~~~~
 
~~~~
To verify results -  top   
~~~~

# What to do if a process is locked 


#STEP 1:  

 
~~~~
ps aux | grep -i apt  

 

sudo kill –9   

 

sudo killall apt apt-get 

~~~~

#STEP2:  

 
~~~~
lsof /var/lib/dpkg/lock  

 

lsof /var/lib/apt/lists/lock  

 

lsof /var/cache/apt/archives/lock  

 

sudo kill -9 PID  

 

sudo rm /var/lib/apt/lists/lock  

 

sudo rm /var/cache/apt/archives/lock   

 

sudo rm /var/lib/dpkg/lock    

 

sudo dpkg --configure -a 
~~~~ 
	
#STEP3:  

 

Troubleshoot: dpkg: error: dpkg frontend is locked by another process 

If you see the error “dpkg frontend is locked by another process” while running the above described method, you’ll have to do an additional step. 

 
~~~~
First, find out the id of the process that is holding the lock file. 

 

lsof /var/lib/dpkg/lock-frontend 

 

The above command will give you the PID of the processes using the lock files. Use this PID to kill the process. 

sudo kill -9 PID 

 

Now you can remove the lock and reconfigure dpkg: 

sudo rm /var/lib/dpkg/lock-frontend sudo dpkg --configure -a  
~~~~

# SSH 
 
~~~~
Configuration for remote server being accessed

eze@ubuntu:~$ sudo apt install openssh-server 
	
eze@ubuntu:~$ sudo systemctl status ssh 
	
eze@ubuntu:~$ sudo ufw allow ssh 
	
root@ubuntu:~# ufw status 
~~~~ 
	
Key Generation: 
~~~~
eze@ubuntu:~$ sudo apt install openssh-server 

eze@ubuntu:~$ sudo apt-get update / yum update (redhat)

eze@ubuntu:~$ sudo apt-get upgrade /yum update (redhat) 

systemctl start sshd   

systemctl status sshd

eze@ubuntu:~$ sudo systemctl status ssh 

eze@ubuntu:~$ sudo ufw allow ssh 

eze@ubuntu:~$ sudo ufw enable 

eze@ubuntu:~$ ssh-keygen -t rsa 

eze@ubuntu:~$ cd .ssh 

eze@ubuntu:~/.ssh$ ssh-keygen 

eze@ubuntu:~/.ssh$ ls 
	
key1 key1.pub 
	
eze@ubuntu:~/.ssh$ ls –ltr 
	
total 8
-rw-r--r-- 1 eze eze 392 Dec 19 16:11 key1.pub
-rw------- 1 eze eze 1679 Dec 19 16:11 key1 

eze@ubuntu:~/.ssh$ ssh-copy-id -i ~/.ssh/key1.pub 192.168.142.136 

eze@ubuntu:~/.ssh$ ssh 192.168.142.136 
~~~~ 
~~~~	
 chmod 600 or 700 for ssh key to work 
~~~~

Copy SSH credentials cat id_rsa.pub | pbcopy 


# SSH File Config

~~~~
Used for multiple users trying to access a box 
 
	1. Create new user using adduser command on the box you want them to have access
~~~~                                                     
                                                      
~~~~
2) use this command to copy the public key to the server you're trying to access:  
   ssh-copy-id -i ~/.ssh/obi_rsa.pub ezeaka01@10.61.240.244 (username@ip_addr) 
~~~~

~~~~
3) nano config in /.ssh directory
  
Edit config file like below: 
 
Config file: 
 
 
Host *
   IdentityFile ~/.ssh/obi_rsa
   User ezeaka01 
 
 
Example: 
 
ssh ezeaka01@10.61.240.244
~~~~ 
 
How to create ssh config 
	
~~~~
      
  ssh 10.61.240.244 -v 
	
  ssh ezeaka01@10.61.240.244 
	
  ll 
	
  ssh-copy-id -i ~/.ssh/obi_rsa.pub ezeaka01@10.61.240.244  
	
  nano config 
  
  Config file: 
 
 
Host * 
	
   IdentityFile ~/.ssh/obi_rsa 
	
   User ezeaka01
  
  ssh 10.61.240.244 
	
  history
 
 
 
~~~~

#File Transfer

~~~~

/usr/bin/scp <app node name>:<filepath> <db node>:<filepath> 

~~~~ 
	
# Troubleshooting 
 

Debugging: 

~~~~
bash -v hello1.sh  
~~~~ 
	
Can't ssh to an app Server:   

~~~~	
- Ping IP from localhost  

- Attempt to ssh from localhost  
	
- Ping IP from another node in the same/another domain  

- Attempt to ssh from that node to node in question  
~~~~
  
~~~~
If the previous 2 fail attempt to log into the server directly e.g. via ILO if it's a physical server like HP-UX series , or directly from Vsphere if a virtual server. If that issue fails, then it's need to be escalated to the infrastructure team/on site team of engineers to diagnose the issue further.  
~~~~
 

#Tip for diagnosing the issue:  

 
~~~~
Notify all the engineers and teams who have been working on the server and check if any of the changes they made could have caused the server's sshd capabilities to stop functioning. E.g. If a certain config file was edited, then revert the changes made to it and test and so forth  
~~~~
 
# Slowness on Server: 

	
Check CPU, RAM, & Swap usage using top command  

 
~~~~
Based on the results the best option is to identify and kill PIDS that is causing the issue and if that is not resolution reboot the node and free up swap space as it doesn't get released after RAM usage goes down 
~~~~

# Git Commands 

 
	
To clone repository 

~~~~	 

git clone <url>  
 
~~~~  

	
1) To add untracked Files - Remember to save the file 1st

~~~~	
git add -i 
	
	
then you see:

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now>
hit 4 (add untracked), then you see

What now> 4
  1: file1
  2: file2
Add untracked>>
	
~~~~	

2) Commit the file 

~~~~

 git commit -m "comment"

~~~~
	
Git add and commit together - For files already present in git 


~~~~

git commit -am "comment"   

~~~~

3) Push changes to repo 

~~~~	 

git push 
 
~~~~ 

Checkout branch 

~~~~	 

git checkout –b <new branch name> 
 
~~~~ 

Discard changes in working directory

~~~~ 

git checkout -- <filename> 

~~~~ 

Check branches  

~~~~ 

git branch   

~~~~ 

Shows the status of the repository

~~~~ 

git status  

~~~~ 

Using Linux in git: 

~~~~ 

git rm  etc 

~~~~ 

Pull in changes from repo: 

~~~~ 

git pull  

~~~~ 

Revert commit:  

~~~~

git revert <git_id> 

~~~~	 

Delete branch: 

~~~~	

git branch -D <branch_name>  

~~~~	 
	
To checkout local changes not yet pushed to git: 

~~~~
	
git checkout filename  
	
~~~~ 

To checkout local changes not yet pushed to git on a different branch:  
	
~~~~

	
git checkout  --filename 
	
~~~~ 
	
Checkout file that is in source control 	

~~~~	
git checkout origin/<branch_name> -- filename	
~~~~ 
	
	
	
	
Remove Files From Git Commit
	
~~~~

In order to remove some files from a Git commit, use the “git reset” command with the “–soft” option and specify the commit before HEAD.

$ git reset --soft HEAD~1 
	
When running this command, you will be presented with the files from the most recent commit (HEAD) and you will be able to commit them.

Now that your files are in the staging area, you can remove them (or unstage them) using the “git reset” command again.

$ git reset HEAD <file>
	
~~~~ 



	
	
	

	
	
# Dealing with conflicts when merging  
	
~~~~ 

• Checkout source branch 
• git merge to destination branch 
• Any conflicts ctrl + f <<<<<< and remove old changes 
• git status 
• git add any changed file 
• git commit + push 
• In vscode select stage change option and save file
	
~~~~  
	
Update Branch locally after deleting in Bitbucket/Github 
~~~~	
 -> git branch -D branch_name 
	
 -> git pull
~~~~	

** LVM ** 

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/lvm.jpg?sanitize=true&raw=true" / 
     
<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/lvm2.png?sanitize=true&raw=true" / 
	
<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/lvm3.png?sanitize=true&raw=true" /
	
