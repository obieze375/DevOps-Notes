# Can't SSH to server as root user

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/can't-ssh-to-server.png?sanitize=true&raw=true"/>


# Cannot CD into a Directory

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/cd-directory.png?sanitize=true&raw=true"/>

# Cannot Open a File Or Run a Script

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/can't-open-file.png?sanitize=true&raw=true"/>

# Cannot Create Links

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/cannot-link.png?sanitize=true&raw=true"/>

# Cannot Write to a File

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/cannot-edit-file.png?sanitize=true&raw=true"/>

# Cannot Change File Permissions / Ownership

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/cannot-change-file-perm.png?sanitize=true&raw=true"/>

# Cannot View Other Users Files

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/cannot-view-other-users-files.png?sanitize=true&raw=true"/>

# Cannot View Other Users Files
<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/Firewall Issue.docx_1.png?sanitize=true&raw=true"/>
<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/Firewall Issue.docx_1.png?sanitize=true&raw=true"/>

<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/Firewall Issue.docx_1.png?sanitize=true&raw=true"/>
<img src="https://raw.githubusercontent.com/obieze375/DevOps-Notes/main/Firewall Issue.docx_1.png?sanitize=true&raw=true"/>

# How to Delete Old Files

• Delete using rm command
• Find files and then delete old files

Command Syntax
~~~~
• find /path/to/files/ -type f -name '*.jpg' -mtime +30 -exec rm {} \;
~~~~

# Explanation

~~~~
• First part is the path where your files are located. 

• Second part -type is the file type f stands for files

• Third part -name is for using the actual file names

• Fourth part -mtime gets how many days the files older then will be listed. +30 is for files older then 30 days.

• Fifth part -exec executes a command. In this case rm is the command, {} gets the filelist and \; closes the command
~~~~

# Filesystem is Corrupted

• Filesystem?

• Types of filesystem

• ext3, ext4, xfs, NTFS etc.

• Filesystem Layout and partitions

• /var, /etc, /root, /home etc.

• Checking filesystem

• df, fdisk –l

# Troubleshooting Steps:

~~~~
• Check /var/log/messages or /var/log/syslog

• Run fsck on the block device (/dev/sda) NOT on mount point

• Unmount filesystem and run fsck
~~~~

# /etc/fstab Corruption

• What is /etc/fstab?

• OS filesystem table

• Understanding /etc/fstab

• Device, mount point, filesystem type, Options, backup, filesystem check order

• Checking filesystem

• df

• Checking or verifying /etc/fstab

• cat, more, vi, vim etc.

• Issue – System is NOT booting

• Incorrect entry in /etc/fstab

• Accidental deletion of /etc/fstab

# Troubleshooting Steps:

• Boot in rescue mode by mounting CD / CD ISO image

• Chose option 1 to mount root filesystem

• Fix the /etc/fstab file

• For deleted file = run blkid



Memory (RAM)
• Random-access memory is a form of computer data storage that stores data 
and machine code currently being used

• Swap (virtual memory)

• Memory carved out of a hard disk. It function just like RAM but it is slower 
than RAM

• Cache

• This memory is typically integrated directly into the CPU chip or placed on a 
separate chip that has a separate bus interconnect with the CPU. The purpose 
of cache memory is to store program instructions and data that are used 
repeatedly

# Troubleshooting Commands:

~~~~
• free –m (mega bytes) or –h (human readable)

• top

• vmstat

• dmesg | grep –i "Out of memory“ (/var/log/messages OR /var/log/syslog)

• Memory commitment in configuration file /etc/sysctl.conf.
~~~~

# Running Out of Memory


# Troubleshooting Steps:

~~~~
• Identify the process causing the memory usage

• top, ps

• Kill or restart the process causing high memory utilization

• kill, service, systemctl

• Prioritize the process

• nice

• Add new swap space

• Create a dedicate file for swap

• Assign it to swap

• Enable swap

• Extend swap space

• Add additional memory from virtualization

• Add additional physical memory.
~~~~

# System Rebooted Or Process Restarted

~~~~
• System reboot/crash

• Memory stress

• CPU stress

• Kernel panic

• Hardware issue

• Process restart

• System reboot

• Process restarted itself (systemctl status process)

• Watchdog application
~~~~

# Troubleshooting Steps:

~~~~
• Login through SSH and the following commands to troubleshoot

• uptime, top, dmesg, iostat -xz 1, journalctl

• Go through the logs

• /var/log/messages, /var/log/syslog, /var/log/boot.log

• For application, check app logs

• Login through console (iLO, iDRAC, virtual console etc.)

• Reach out to the vendor (e.g. Redhat, SUSE, Oracle etc.)

• For hardware, check logs from the console and reach out to the vendor.
~~~~

# Unable to get an IP Address


# Troubleshooting Steps:
~~~~
• Check your DHCP server (Modem at home)

• Check network setting at virtualization level

• Check interface at the hardware level

• lspci | egrep -i 'eth|wifi|wireless'

• nmcli -p dev

• Check your interface (ifconfig or ip addr)

• Check whether you are connected as wireless or wired network

• Difference between ifup <interface> and ifconfig up <interface>

• Restart network service systemctl restart network

• For static IP verify the network configuration files

• /etc/sysconfig/network-scripts/ifcfg-enp0s3 or ifcfg-eth0

• DEVICE=eth0

• BOOTPROTO=none

• ONBOOT=yes

• PREFIX=24

• IPADDR=192.168.1.200
~~~~

# IP Address Assigned but not Reachable

# Troubleshooting Steps:
~~~~
• Check if you are on the correct network interface (ifconfig)

• Check to see if you got the right subnet mask or gateway

• Ping the gateway

• Check if the gateway is assigned (netstat –rnv)

• Check with network team if the correct vLAN is assigned on the switch side

• Run ethtool or mii-tool to check the NIC status

• Run ifup <interface> command to bring the NIC port up

• Restart network systemctl restart network

• Check on the status of NIC by running ifconfig or ip addr command

• Check to see if the IP is assigned to some other device (IP conflict)

• Turn off firewall
~~~~

# Having Trouble Using vi Editor


# Troubleshooting Steps:

~~~~
• Permissions issues

• Ownership

• File is already open for editing

• Arrow keys vs. hjkl (h=left, j=up, k=down, l=right)

• Use vim editor instead of vi.
~~~~

# Cannot Run Certain Commands



# Troubleshooting Steps:
~~~~
• Permissions and ownership issues

• Relative path vs. Absolute path

• Command paths not defined (echo $PATH)

• Command packages missing or not installed

yum provides pwd
yum search telnet

• Command library missing or deleted (whereis).

~~~~

# Cannot Change Password

~~~~
• Two important files for password
(/etc/passwd and /etc/shadow)

• Issues:

• User is added manually in /etc/passwd file and /etc/shadow 
file has no information (passwd user)

• /etc/shadow file is corrupted

• /etc/shadow file is missing (pwconv will recreate the file)
~~~~

# Troubleshooting Steps:

~~~~
• Correct user

• Provide current password first before entering new password

• You have to be root to set other user passwords

• Make sure to specify the user after passwd command

• Make sure to run pwconv after creating a user in /etc/passwd file

• Fix the /etc/shadow file

• Run the pwconv command to recreate the /etc/shadow file. (Remember you will have to setup passwords for each user again)
~~~~

# User Has No Home Directory

• What is home directory?

• Issues:
• No home directory when user login

# Troubleshooting Steps:

~~~~
• Directory does not exist

• Directory permissions and ownership

• Directory name should match with directory listed in /etc/passwd
~~~~

# How to Change Every Instance of a Word in a File


# Troubleshooting Steps:

~~~~
• Manually change every word

• vi the file and use :s = for substitution (:1,$s/string/replacingstring/)

• Use the sed command (sed 's/string/newstring/g‘)
~~~~

# How to Use sed Command


# Replace a string in a file with a newstring
~~~~
sed 's/string/newstring/g'
~~~~

# Replace a string in a file and save it 

~~~~
sed –i ‘s/string/newstring/g’ filename
~~~~

# Remove the first line in a file 

~~~~
sed ‘1d’ file.out
~~~~

# Replace a string during vi :

~~~~
1,$s/string/replacingstring/
~~~~

# Remove spaces 

~~~~
sed -i 's/ //g' file.txt
~~~~

# Add TAB instead of space 

~~~~
sed -i 's/ /{--TAB--]/g' file.txt

In place of --TAB-- , give CTRL + V 
followed by TAB
~~~~

# Add a line before the 4th line of the line

~~~~
sed ‘4 i\ newstring’ filename
~~~~

# Insert a line before matching word 

~~~~
sed ‘/string/i \newstring’ filename
~~~~

# How to Kill a Process, User or Terminal


# Troubleshooting Steps:

~~~~
• Find the process ID (ps –ef)

• Run kill PID

• Run kill -9 PID

• Run pkill ProcessName

• Run killall
~~~~


# System is Running Slow

• Understanding the problem
• Processing
• Disk writing
• Networking (file transfer etc.)
• Hardware

# Troubleshooting Steps:

~~~~
• Check if the right system is reported or you are on the right system

• Check disk space (df –h, du)

• Check processing (top, free, lsmem, /proc/meminfo, vmstat, pmap <PID>, dmidecode, lscpu or /proc/cpuinf)

• Check disk issues (iostat –y 5, lsof)

• Check networking (tcpdump –i enps03, lsof -i -P -n | grep -i listen, netstat –plnt or ss –plnt, iftop)

  yum install epel-release

• Check system uptime (uptime) # yum install iftop

• Check logs

• Check hardware status by logging into system console

• Other tools (htop, iotop, iptraf, psacct)
~~~~

# Rollback Updates and Patches

~~~~
• Virtual machine

• Physical machine

• Rollback a package or patch

• yum install <package-name>

• yum history undo <id>

• Rollback an update

• Downgrading a system to minor version (ex: RHEL7.1 to RHEL7.0) is not recommended as this might leave the system in undesired or unstable state

• yum update= Update will preserve them 

• yum upgrade = Upgrade will delete obsolete packages

• yum history undo <id>
~~~~
