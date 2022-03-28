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