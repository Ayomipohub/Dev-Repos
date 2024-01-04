# LINUX PRACTICE PROJECT

## 'sudo' command

 sudo is designed to enable a permitted user to execute a command as the superuser while providing a record of the command and its arguments for auditing purposes. It also allows system administrators to control which users are allowed to run specific commands.


When you execute this command 'sudo apt upgrade', apt will check for updates for all installed packages on your system and prompt you to confirm whether you want to proceed with the upgrade. If updates are available, it will download and install them.

![Alt text](<images/sudo cmd.PNG>)

# pwd command

## pwd entails print out name of current/working directory.When you execute this command, it will output the absolute path of the directory you are currently in

![Alt text](<pwd cmd.PNG>)



The pwd command is a helpful tool for understanding your location within the directory structure, and it is commonly used in shell scripts and command-line operations.

# `cd` command


## cd command, which stands for "change directory," is used in Linux, to change the current working directory. It allows you to navigate through the file system by moving from one directory to another.


### If you run cd without any arguments, it will take you to your home directory. If you provide a directory name as an argument, it will change your current working directory to that specified directory.
![Alt text](<images/cd cmd2.PNG>)



# 'ls' COMMAND

## ls command is used to list the files and directories in the current working directory. It provides a way to view the contents of a directory from the command line.
![Alt text](<images/ls cmd1.PNG>)


If you run ls without any arguments, it will list the files and directories in the current working directory.

![Alt text](<images/ls cmd1.PNG>)

# 'cat' COMMAND

## The cat command is used  to concatenate and display the contents of one or more files. 
![Alt text](<images/cat cmd.PNG>)


# The 'cp' command


## The cp command is used to copy files and directories from one location to another.

### -r (or -R): Copy directories recursively. This is necessary when copying directories and their contents.

![Alt text](<images/cp cmd.PNG>)

# The 'mv' command


## mv command is used to move or rename files and directories

![Alt text](<images/mv cmd.PNG>)



# mkdir command

## mkdir command is used to create directories (folders)
![Alt text](<images/mkdir cmd.PNG>)



# 'rmdir' command

## rmdir command is used to remove empty directories. Unlike the rm command, which can delete files and non-empty directories.

![Alt text](<images/rmdir cmd.PNG>)

 # `rm` COMMAND

## rm command is used to remove (delete) files and directories.
![Alt text](<images/rm cmd.PNG>)


# 'touch' COMMAND

 ## touch command is used to create empty files and update the access and modification timestamps of existing files.
![Alt text](<images/touch cmd.PNG>)

# `locate` COMMAND

## locate command  is used to quickly find the location of files and directories on the system.
![Alt text](<images/locate cmd.PNG>)

# `find` command


## find command is a powerful tool for searching and locating files and directories based on various criteria.
![Alt text](<images/find cmd.PNG>)


# `grep` COMMAND

## grep command  is a powerful tool used for searching and pattern matching in text files.
![Alt text](<images/grep cmd.PNG>)

# `df` COMMAND

## df command is used to display information about the disk space usage on mounted file systems.
![Alt text](<images/df cmd.PNG>)

# `du` COMMAND

## du command is used to estimate the disk space usage of files and directories. It is used to estimate the disk space usage of files and directories
![Alt text](<images/du cmd.PNG>)

# `head` command

## head command is used to display the beginning (or "head") of a text file or the output of a command. By default, it shows the first 10 lines of a file or the output of a command. 
![Alt text](<images/head cmd.PNG>)

# `tail` command

## tail command is used to display the end (or "tail") of a text file or the output of a command. By default, it shows the last 10 lines of a file or the output of a command.
![Alt text](<images/tail cmd.PNG>)

# `diff` command

## diff command  is used to compare the contents of two files and display the differences between them. 
![Alt text](<images/diff cmd#.PNG>)

# `tar` COMMAND

## tar command is used for archiving files and directories. It creates a single archive file (often compressed) that can be easily transported or stored. The name "tar" stands for "tape archive," reflecting its historical use in creating archives for tape backups. 
![Alt text](<images/tar cmd.PNG>)

# `chmod` COMMAND

## chmod command is used to change the permissions (read, write, execute) of files and directories. 
![Alt text](<images/chmod cmd.PNG>)

# `jobs` command

## jobs command s used to display the status of background jobs that are currently running in the shell. When you run a command in the background by appending an ampersand (&) at the end of the command, it runs asynchronously, allowing you to continue working in the shell.
![Alt text](<images/jobs cmd.PNG>)

# `kill` command

## kill command is used to send signals to processes. The primary purpose of the kill command is to terminate or signal processes, allowing users to control or interrupt the execution of running programs. 
![Alt text](<images/pid cmd.PNG>)
![Alt text](<images/kill cmd#.PNG>)

# `ping` command

## ping command command is a network utility tool used to test the reachability of a host on an Internet Protocol (IP) network and to measure the round-trip time for messages sent from the originating host to a destination computer.
![Alt text](<images/ping cmd.PNG>)

# `wget` command

## wget command is a command-line utility for downloading files from the web. It is available on Unix-like operating systems, including Linux, and can be used to retrieve files using various protocols such as HTTP, HTTPS, FTP, and FTPS. 

![Alt text](<images/wget cmd.PNG>)


# `uname` command
## uname command is used to display system information. It provides details about the operating system and the system hardware.

![Alt text](<images/uname cmd.PNG>)


# `top` command 

## top command is a real-time system monitoring tool that provides an interactive, dynamic view of system processes. It displays a constantly updated list of processes, their resource usage, and other system information.
![Alt text](<images/top cmd.PNG>)


# `history` command

## history command is used to display a list of previously executed commands from the command-line history. It provides a record of the commands that have been entered in the current session or in previous sessions, depending on the configuration.
![Alt text](<images/history cmd.PNG>)


# `man` command

## man command is used to display the manual pages (documentation) for commands, utilities, and system functions. The manual pages provide detailed information about how to use and understand a particular command or feature. 
![Alt text](<images/man cmd.PNG>)


# `echo` command
## echo command  is used to display text or variables in the terminal. It is a simple command that outputs its arguments to the terminal. 
![Alt text](<images/echo cmd.PNG>)


# `zip and unzip` command

## zip command is used in Unix-like operating systems, including Linux, to compress and archive files into a Zip format. while unzip is used to extract and decompress files from a ZIP archive. 

![Alt text](<images/zip cmd.PNG>)


# `hostame` command
## hostname is used to query or set the system's host name.

![Alt text](images/hostname.PNG)


# `useradd and userdel` command

## user add command is used to create a new user account. It is a command-line utility that adds or updates user information in the system files. while user del is used to delete a user account. When a user account is deleted using userdel, the user's home directory and mail spool may also be deleted, depending on the options used. 
![Alt text](<images/useradd cmd.PNG>)


# `apt-get` command

## apt-get is a package management tool used in Debian-based Linux distributions, including Ubuntu. It is part of the Advanced Package Tool (APT) system and is used for installing, upgrading, and managing software packages on a Linux system. 

![Alt text](images/apt-get.PNG)


# `nano, vi , jed` command

## nano is a simple and user-friendly text editor. It is designed to be easy for beginners to use and provides a straightforward interface.


![Alt text](<images/nano cmd.PNG>)


### vi  is a powerful and widely used text editor that is part of most Unix-like systems. It has modes for editing, command, and visual modes, which provide different functionalities.
![Alt text](<images/vi cmd.PNG>)


#### jed is a programmer's text editor that is part of the SLang library. It provides features similar to Emacs and is extensible through the S-Lang scripting language.
![Alt text](<images/jed cmd.PNG>)


# `alias, unalias` command

## alias and unalias are used to create and remove command aliases. An alias is a user-defined shortcut or alternate name for a command or a sequence of commands. Aliases can be helpful for creating shorter or more convenient names for commonly used commands.

![Alt text](<images/alias cmd.PNG>)


# `su` command
## su command short for "switch user" or "substitute user," is used in Unix-like operating systems, including Linux, to change the current user context to that of another user. By default, if no specific user is specified, it attempts to switch to the superuser (root) account.

![Alt text](<images/su cmd.PNG>)


# `htop` command

## The htop command is an interactive process viewer and system monitor for Linux. It provides a more user-friendly and feature-rich alternative to the traditional top command. htop allows you to view and manage system processes in a dynamic and visually appealing way.

![Alt text](<images/htop cmd.PNG>)


# `ps` command

## The ps command is used to display information about currently running processes. It provides a snapshot of the processes running on the system at the time the command is executed. 

![Alt text](<images/pid cmd.PNG>)



Thank you









