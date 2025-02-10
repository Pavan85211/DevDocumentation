## what are important linux commands in devops explain it?
In DevOps, Linux commands are essential for managing servers, deploying applications, automating tasks, monitoring system performance, and more. Here are some important Linux commands used in DevOps along with brief explanations of their functionalities:
1. ssh: Stands for Secure Shell. It is used to establish a secure connection to a remote server. DevOps engineers often use SSH to access servers for configuration, deployment, or troubleshooting.
    Example: `ssh username@hostname`
2. scp: Stands for Secure Copy. It allows you to securely copy files between a local and remote host or between two remote hosts.
    Example: `scp local_file username@hostname:/remote/directory`
3. rsync: Similar to `scp`, but it's more efficient for synchronizing files and directories between local and remote systems. It only transfers the parts of files that have changed, reducing the bandwidth required.
    Example: `rsync -avz /local/directory username@hostname:/remote/directory`
4. wget/curl: Both are used for downloading files from the internet. `wget` is a command-line utility for non-interactive downloading files from the web. `curl` is a tool to transfer data from or to a server, supporting various protocols.
    Example: `wget http://example.com/file.zip`
5. grep: Stands for Global Regular Expression Print. It's used to search text or files for patterns. It's commonly used with other commands through piping to filter output.
    Example: `grep "pattern" file.txt`

6. awk: A versatile programming language primarily used for pattern scanning and processing. It's particularly useful for processing structured text data, like logs.
    Example: `awk '{print $1}' file.txt`
7. sed: Stands for Stream Editor. It's used for filtering and transforming text. It's often used to perform search and replace operations on text files.
    Example: `sed 's/old_text/new_text/g' file.txt`
8. tar: Stands for Tape Archive. It's used to create and extract archives. It's often used in combination with compression tools like gzip or bzip2.
    Example: `tar -czvf archive.tar.gz directory`
9. top/htop: These commands are used for monitoring system resources such as CPU, memory, and processes. `top` provides a dynamic real-time view of system processes. `htop` is an interactive process viewer that provides a more user-friendly interface compared to `top`.
    Example: `top` or `htop`
10. systemctl: It's used to manage systemd services on Linux systems. You can use it to start, stop, enable, disable, and check the status of services.
    Example: `systemctl status service_name`
These commands represent just a fraction of the many tools available in the Linux environment, but they are particularly essential for DevOps tasks. Understanding how to effectively use these commands can greatly improve efficiency and productivity in managing infrastructure and deploying applications.

## file commands in Linux.
File commands in Linux are essential for managing files and directories, viewing file contents, and performing various file operations. Here's a list of some important file commands in Linux:
1. ls: Lists the contents of a directory.
    Example: `ls`, `ls -l`, `ls -a`
2. pwd: Prints the current working directory.
    Example: `pwd`
3. cd: Changes the current directory.
    Example: `cd directory_name`, `cd /path/to/directory`
4. mkdir: Creates a new directory.
    Example: `mkdir directory_name`
5. rm: Removes files or directories.
    Example: `rm file.txt`, `rm -r directory`
6. cp: Copies files or directories.
    Example: `cp file.txt /path/to/destination`, `cp -r directory /path/to/destination`
7. mv: Moves or renames files or directories.
    Example: `mv file.txt new_location/file.txt`, `mv old_name.txt new_name.txt`
8. cat: Concatenates and displays file content.
    Example: `cat file.txt`
9. more: Displays file content page by page.
    Example: `more file.txt`
10. less: Displays file content with backward navigation support.
    Example: `less file.txt`
11. head: Displays the first few lines of a file.
    Example: `head file.txt`
12. tail: Displays the last few lines of a file.
    Example: `tail file.txt`
13. touch: Creates an empty file or updates file timestamps.
    Example: `touch file.txt`
14. chmod: Changes file permissions.
    Example: `chmod 755 file.txt`
15. chown: Changes file ownership.
    Example: `chown user:group file.txt`
16. ln: Creates links to files.
    Example: `ln -s /path/to/target link_name`
17. find: Searches for files and directories.
    Example: `find /path/to/search -name "pattern"`
18. grep: Searches for patterns in files.
    Example: `grep "pattern" file.txt`
19. wc: Counts lines, words, and characters in a file.
    Example: `wc file.txt`
20. file: Determines the file type.
    Example: `file file.txt`

## Working with Directories
You can create the directory in linux using mkdir command.

•If you want to  create a murali directory.
•mkdir murali
•If you want to create a sub directories.
•mkdir –p /opt/sunil/naresh/sivaLearn 

Working with cp command
•cp command is used to copy the file or directory from one directory to another directory or same directory.
•Example: Copy the file from /root to /opt directory
•cp murali /opt
•Copy the directory from /root  to /opt directory
•cp -r naresh/ /optLearn 


## What is Softlink in linux?
•A symbolic or soft link is an actual link to the original file, If you delete the original file, the soft link has no value, because it points to a non-existent file.•To create the softlink use below command
•ln –s originalname softlinkname•
We can create the softlink for both files and directories.
•Both originalfile and softlinkfile  inode numbers are same.

## What is Hardlink in linux?
•Hard link is a mirror copy of the original file. But in the case of hard link, it is entirely opposite. 
•Even if you delete the original file, the hard link will still has the data of the original file. 
•Because hard link acts as a mirror copy of the original file.•To create the softlink use below command
•ln originalname hardlinkname•Both originalfile and hardlinkfile  inode numbers are same.
•We can create  hardlink ,only for files.

## Working with File Permissions
•All the three owners (user, group, others) in the Linux system have three types of permissions defined. 
•Example:•drwxr-xr-x 10 root root     4096 May 27 14:41 kubectx/
•Nine characters denotes the three types of permissions.•Read(r) - 4•Write(w)- 2•Execute(x)- 1
•Example: chmod 777 filename
•Owner = rwx
•Group =  rwx
•Others = rwx


##  Working with File Ownership
•The chown command allows you to change the user and/or group ownership of a given file, directory, or symbolic link.
•Example:
•drwxr-xr-x 10 root root     4096 May 27 14:41 kubectx/
•In Linux, all files are associated with an owner and a group and assigned with permission access rights for the file owner, the group members, and others.
•In this tutorial, we will show you how to use the chown command.
•Example: chown user1:group1 filename


## Working with rm command
•rmcommand is used to remove a file and directory in linux.
•To remove a file use below command•rm –f filename
•To remove a directory use below command•rm –rf filename
•Note:•r= recursively •f= forcefully



## How to create and delete the users in Linux?
•If you want to create the user.•useradd user_name (or) adduser user_name
•If you want to check whether user created or not.
•id user_name (or) cat /etc/passwd•If you want to delete the user
•userdel -r user_name

•Note:•r =  remove home directory and mail spool

## How to create and delete groups in linux?
•If you want to create the group.
•groupadd group_name
•If you want to check whether user created or not.
•cat /etc/group•If you want to delete the user.
•groupdel group_name


## Adding the users in group
•Using usermod command to add the users in exiting group.
•Example:
•usermod –a –G group_name user_name


## What is head command in Linux?
•The head command is print the top N number of data of the given input.
 •By default, it prints the first 10 lines of the specified files. 
•Example:head filename•-n num: Prints the first ‘num’ lines instead of first 10 lines. 
num is mandatory to be specified in command otherwise it displays an error.
•Example: head –n 5 filename


## What is tail command in Linux?
●Linux tail command is used to display the last ten lines of one or more files. 
●Its main purpose is to read the error message. By default, it displays the last ten lines of a file.
●Example: tail filename
●The '-n' option displays the specified number of lines. 
To specify the number of lines, execute the command:
●Example:○tail –n 5 filename


## Working with top command
•top command is used to show the Linux processes. 
•It provides a dynamic real-time view of the running system. 
•Usually, this command shows the summary information of the system and the list of processes or threads which are currently managed by the Linux Kernel.
•Example:top



## What is find command in Linux?
•find command is  used to find the files and directories and perform subsequent operations on them. 
•It supports searching by file, folder, name, creation date, modification date, owner and permissions.

find command examples
•Find the murali.txt file in a current working directory.
•find . -name murali.txt•Find files under /opt directory
•find /opt -name muni.txt•Find files using name and ignoring case under /opt directory
•find /opt -iname sunil.txt•Note:i - ignore case sensitive
•Find directories under /opt directory•find  /opt -type d -iname suresh

find command examples
•Find all .txt files  under the /opt directory
•find /opt -iname "*.txt"•Find all Empty Files under /root directory
•find /root -type f  -empty
•Find all Empty directories•find / -type d –empty


## What is df command•df stands for disk free. 
•Using df command to check weather space is available or not in server•Example:
•df -h•Note: h = human readable format
•To check all the filesystems•Example:
•df -a
•Note: a = all


## What is du command
•du command is used to display the disk usage. 
•Example:•du -h
•Note: h =human readable format
•If you want to check specific directory.
•Example: in /root directory•du /root -h

## What is ps command in Linux?
•The ps stands  for Process Status
•ps is a command line utility that is used to display or view information related to the processes running in a Linux system.
•To check whether the process is running or not use below command.
•ps –ef | grep 8080

## ps command with example
•Display the Processes Running in the Current Shell•ps
•Display All the Currently Running Processes
•ps -A
•Note: A = all
•Display All the Processes Associated with the Current Terminal
•ps -T
•Display All the Processes Associated with a Particular User
•ps -u tomcat

## What is kill command and with examples in Linux?
•kill command is used to  terminate a process is kill command.
• You need to know the PID of the process you want to terminate.
•The kill -9 command sends a SIGKILL signal indicating to a service to shut down immediately. An unresponsive program will ignore a kill command, but it will shut down whenever a kill -9 command is is used.
•Example: kill -9 PID
•kill -3 is a thread dump that will list all the Java threads that are currently active in Java Virtual Machine (JVM).•Example: kill -3 PID


## Telnet and establish a connection
Telnet can be used to check whether or not a port on the Voyager server is open to you.telnet <hostname></hostname>
telnet 127.0.0.1 22
Netstat command in Linux
The netstat command is like a special tool in Linux that helps you understand and check things about how your computer connects to the internet. 
`netstat` stands for network statistics. It allows users to display network-related information and diagnose various networking issues.
Show Both Listening and Non-listening Sockets Using netstat Command in Linux
-a -all : Show both listening and non-listening sockets. With the –interfaces option, show interfaces that are not up.
netstat -a | more
List Only Listening Ports Using netstat Command in Linux
netstat -l
List Only Listening TCP Ports Using netstat Command in Linux
netstat -lt


