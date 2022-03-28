--- 
layout: page 
title: Linux 
permalink: /Linux/ 

--- 

Bash Alias
-----------

# ----------------------
# Git Aliases
# ----------------------
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
# ----------------------
# Git Functions
# ----------------------
# Git log find by commit message
function glf() { git log --all --grep="$1"; }

From <https://jonsuh.com/blog/git-command-line-shortcuts/>  

# ----------------------
# How to create aliases
# ----------------------
# Git log find by commit me

1. Edit ~/.bash_aliases or ~/.bashrc file using: vi ~/.bash_aliases
2. Append your bash alias
3. For example append: alias update='sudo yum update'
4. Save and close the file.
5. Activate alias by typing: source ~/.bash_aliases

Please note that ~/.bash_aliases file only works if the following line presents in the ~/.bashrc file:
if [ -f ~/.bash_aliases ]; then
. ~/.bash_aliases
fi
Are above lines are missing in your ~/.bashrc file? Just append at the end of the ~/.bashrc, using a text editor such as vi/vim or joe. 
Examples
Let us create four aliases as follows:
$ vi ~/.bash_aliases
OR
$ joe ~/.bashrc
Append text:
# update our debian/ubuntu box
alias update='sudo -- sh -c "apt update && apt upgrade"'
 
# make grep output colorful 
alias grep='grep --color=auto'
 
# set eth0 as an interface for eth0  
alias vnstat='vnstat -i eth0'
 
# flush redis cache for wp
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




##############################################################################
# DEBUGGING SHELL PROGRAMS
##############################################################################


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

# ----------------------
# For Loops 
# ----------------------   

for x in {1..10}
do
  statements
done

for name [in list]
do
  statements that can use $name
done

for (( initialisation ; ending condition ; update ))
do
  statements...
done

# ----------------------
# Functions 
# ----------------------  

# The function refers to passed arguments by position (as if they were positional parameters), that is, $1, $2, and so forth.
# $@ is equal to "$1" "$2"... "$N", where N is the number of positional parameters. $# holds the number of positional parameters.


function functname() {
  shell commands
}

Example: 


1. #!/bin/bash
2. # Basic function
3. print_something () {
4. echo Hello I am a function
5. }
6. print_something
7. print_something

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php> 





	• unset -f functname  # deletes a function definition 
	
	• declare -f          # displays all defined functions in your login session



1. #!/bin/bash
2. # Passing arguments to a function
3. print_something () {
4. echo Hello $1
5. }
6. print_something Mars
7. print_something Jupiter

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php> 


1. #!/bin/bash
2. # Setting a return status for a function
3. print_something () {
4. echo Hello $1
5. return 5
6. }
7. print_something Mars
8. print_something Jupiter
9. echo The previous function has a return value of $?

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php> 

1. #!/bin/bash
2. # Experimenting with variable scope
3. var_change () {
4. local var1='local 1'
5. echo Inside function: var1 is $var1 : var2 is $var2
6. var1='changed again'
7. var2='2 changed again'
8. } 

9. var1='global 1'
10. var2='global 2' 

11. echo Before function call: var1 is $var1 : var2 is $var2 

12. var_change 

13. echo After function call: var1 is $var1 : var2 is $var2

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php>  


# ----------------------
# If Statement
# ----------------------


if condition
then
  statements
[elif condition
  then statements...]
[else
  statements]
fi

1. #!/bin/bash
2. # else example
3. if [ $# -eq 1 ]
4. then
5. nl $1
6. else
7. nl /dev/stdin
8. fi

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

1. #!/bin/bash
2. # or example
3. if [ $USER == 'bob' ] || [ $USER == 'andy' ]
4. then
5. ls -alh
6. else
7. ls
8. fi

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 


1. #!/bin/bash
2. # Basic if statement
3. if [ $1 -gt 100 ]
4. then
5. echo Hey that\'s a large number.
6. pwd
7. fi
8. date

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

1. #!/bin/bash
2. # elif statements
3. if [ $1 -ge 18 ]
4. then
5. echo You may go to the party.
6. elif [ $2 == 'yes' ]
7. then
8. echo You may go to the party but be back before midnight.
9. else
10. echo You may not go to the party.
11. fi

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

1. #!/bin/bash
2. # Nested if statements
3. if [ $1 -gt 100 ]
4. then
5. echo Hey that\'s a large number.
6. if (( $1 % 2 == 0 ))
7. then
8. echo And is also an even number.
9. fi
10. fi

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

1. #!/bin/bash
2. # and example
3. if [ -r $1 ] && [ -s $1 ]
4. then
5. echo This file is useful.
6. fi

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php>  


# ----------------------
# INPUT/OUTPUT REDIRECTORS
# ----------------------



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

# ----------------------
# Operators
# ----------------------



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


# ----------------------
# Process Handling
# ---------------------- 

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


# ----------------------
# Strings
# ---------------------- 


	• str1 == str2               # str1 matches str2 
	
	• str1 != str2               # str1 does not match str2 
	
	• str1 < str2                # str1 is less than str2 (alphabetically) 
	
	• str1 > str2                # str1 is greater than str2 (alphabetically) 
	
	• str1 \> str2               # str1 is sorted after str2 
	
	• str1 \< str2               # str1 is sorted before str2 
	
	• -n str1                    # str1 is not null (has length greater than 0) 
	
    -z str1                    # str1 is null (has length 0) 

# ----------------------
# Switchcase
# ---------------------- 

    case expression in
  pattern1 )
    statements ;;
  pattern2 )
    statements ;;
esac

1. #!/bin/bash
2. # case example
3. case $1 in
4. start)
5. echo starting
6. ;;
7. stop)
8. echo stoping
9. ;;
10. restart)
11. echo restarting
12. ;;
13. *)
14. echo don\'t know
15. ;;
16. esac

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php> 

1. #!/bin/bash
2. # Print a message about disk useage.
3. space_free=$( df -h | awk '{ print $5 }' | sort -n | tail -n 1 | sed 's/%//' )
4. case $space_free in
5. [1-5]*)
6. echo Plenty of disk space available
7. ;;
8. [6-7]*)
9. echo There could be a problem in the near future
10. ;;
11. 8*)
12. echo Maybe we should look at clearing out old files
13. ;;
14. 9*)
15. echo We could have a serious problem on our hands soon
16. ;;
17. *)
18. echo Something is not quite right here
19. ;;
20. esac

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php>   


# ----------------------
# Until
# ---------------------- 

until condition; do
  statements
done

1. #!/bin/bash
2. # Basic until loop
3. counter=1
4. until [ $counter -gt 10 ]
5. do
6. echo $counter
7. ((counter++))
8. done
9. echo All done

From <https://ryanstutorials.net/bash-scripting-tutorial/bash-loops.php#while> 