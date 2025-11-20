# TryHackMe - Linux Fundamentals Part
* Date: 19-11-2025 to 20-11-25
* Level: Beginner

## Accessing Linux Machine Using SSH (Deploy)

What is SSH & how does it work?
Secure shell or SSH simply is a protocol between devices in an encrypted form. Using cyptography, any input we send in a human-readable format is encrypted for travelling over a network--where it is then unencrypted once it reaches the remote machine.

## Using SSH to login to Linux machine
The syntax to use SSH is very simple. We only need to provide two things:
1. The IP address of the remote machine
2. Correct credentials to a valid account to login with on the remote machine

## Introduction to Flags and Switches
A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches. When using a command, unless otherwise specified, it will perform its default behaviour.
For example, <em>ls</em> lists the contents of the working directory. However, hidden files are not shown. We can use flags switches to extend the behaviour of commands.

## The Man(ual) Page
The manual page are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself and online.

## File System Interaction (Continuation)
More commands for interacting with the filesystem to allow us to:
* Create files and folders
* Move files and folders
* Delete files and folders
More specifically, the following commands

| Command | Full Name | Purpose |
| ------- | --------- | -------- |
| touch | touch | Create file |
| mkdir | make directory | Create a folder |
| cp | copy | Copy a file or folder |
| mv | move | Move a file or folder |
| file | file | Determine the type of a folder |

<em><i>Protip: Similarly to using cat. we can provide full file paths, i.e. directory1/directory2/note for all of these commands</i></em>

## Permissions 101
A file or folder can have a couple of characterisitics that determine both what it is that and who we can do with it as -- such as the following:
* Read
* Write
* Execute

* - rwx rwx rwx - The first "rwx" means read, write and execute permissions for the file owner, second means group owner has permissions to read write and execute, while the third "rwx" means read, write and execute permissions for the file owner. The "-" indicates the regular file, <em><i>d</i></em> indicates directory.
 
## The Differences Between Users & Groups
The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.

Let's put this into a real-world context; the system user that runs a web server must have permissions to read and write files for an effective web application. However, companies such as web hosting companies will have to want to allow their customers to upload their own files for their website without being the webserver system user--compromising the security of every other customer. 

## Switching Between Users
Switching between users on a Linux install is easy work thanks to the <em>su</em> command. Unless you are the root user (or using root permissions through sudo), then you are required to know two things to facilitate this transition of user accounts:
* The user we wish to switch to
* The user's password
The <em>su</em> command takes a couple of switches that may be of relevance to you.

## Common Directories
/etc
This root directory is one of the most important root directories on your system. The etc folder (short for etcetera) is a commonplace location to store system files that are used by your operating system. 
/var 
The "/var" directory, "var" being short for variable data, is one of the main root folders found on a Linux install. This folder stores data that is frequently access or written by services or applications running on the system. For example, log files from running services and applications are written here (/var/log), or other data that is not necessarily associated with a specific user (i.e, databases and the like).

/root 
Unlike the /home directory, the <em>/rootfolder</em> is actually the home for the "root" system user. There isn't anything more to this folder other than just understanding that this is the home directory for the "root" user. But, it is worth a mention as the logical presumption is that this user would have their data in a directory such as "/home/root" by default.

/tmp
This is a unique root directory found on a Linux install Short for "temporary", the /tmp directory is volatile and is used to store data that is only needed to be accessed once or twice. Similar to the memory on your computer, once the computer is restarted, the contents of this folder are cleared out.
What's useful for us in pentesting is that any user can write to this folder by default. Meaning once we have access to a machine, it serves as a good place to store things like our enumeration scripts.



## Lab (SSH)
The command to do this is <em>ssh</em> and then the username of the account, <em>@</em> the IP address of the machine we want to access remotely. For example <em><i>ssh tryhackme@10.10.137.96</i></em>. Once executed we will then be asked to trust the host and then provide 
a password for the "tryhackme" account.

<img width="913" height="752" alt="image" src="https://github.com/user-attachments/assets/dcbe3e89-c154-4306-9499-33e648edd381" />

## Lab (Flags & Switches)
Using our <em>ls</em> as example, <em>ls</em> informs us that there are folder named folder1, folder2, folder3, folder4. However, after using the <em>-a</em> argument (short for <em>--all</em>, we now suddenly have an output with a few more files and folders such as
".hiddenfolder". Files and folders with "." are hidden files.
<i>Note: Commands that accept these will also have a <em>--help</em> option. This option will list the possible options that the command accepts, provide a brief description and example of how use it.</i>
<img width="838" height="128" alt="image" src="https://github.com/user-attachments/assets/18fd08ea-e36c-46d0-b86c-fe87198871ae" />
<img width="921" height="610" alt="image" src="https://github.com/user-attachments/assets/b2aa196e-29dc-4dfc-8eb8-f2f195c4ce26" />

## Lab (Manual Page)
To access this documentation, we can use the <em>man</em> command and then provide the command we want to read the documentation for. Using our <em>ls</em> example, we would use <em>man ls</em> to view the manual pages for <em>ls</em>,
<img width="926" height="732" alt="image" src="https://github.com/user-attachments/assets/c157da32-bc21-4d96-81c6-0c5d3a528994" />

## Lab (File System Interaction (Continuation) )
In this lab, the commands <em>ls, mkdir, cp, mv, rm, echo</em> were all used.

<img width="847" height="737" alt="image" src="https://github.com/user-attachments/assets/fa2e83b0-bd70-4137-afe4-2d1b0042bd6d" />

## Lab (Common directories)
Testing the common directories on TryHackMe Lab
* cd /etc
* cd /var
* cd /tmp
* cd /root

<img width="771" height="727" alt="image" src="https://github.com/user-attachments/assets/f79df20b-0f04-493e-9ad7-bc704b8c3d1a" />
<img width="906" height="370" alt="image" src="https://github.com/user-attachments/assets/92a94877-a525-4622-a19f-529cc0392351" />












