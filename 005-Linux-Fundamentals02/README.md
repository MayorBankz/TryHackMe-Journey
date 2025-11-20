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



## Lab (SSH)
The command to do this is <em>ssh</em> and then the username of the account, <em>@</em> the IP address of the machine we want to access remotely. For example <em><i>ssh tryhackme@10.10.137.96</i></em>. Once executed we will then be asked to trust the host and then provide 
a password for the "tryhackme" account.

<img width="913" height="752" alt="image" src="https://github.com/user-attachments/assets/dcbe3e89-c154-4306-9499-33e648edd381" />

## Lab (Flags & Switches)
Using our <em>ls</em> as example, <em>ls</em> informs us that there are folder named folder1, folder2, folder3, folder4. However, after using the <em>-a</em> argument (short for <em>--all</em>, we now suddenly have an output with a few more files and folders such as
".hiddenfolder". Files and folders with "." are hidden files.
<i>Note: Commands that accept these will also have a <em>--help</em> option. This option will list the possible options that the command accepts, provide a brief description and example of how use it.</i>

## Lab (Manual Page)
To access this documentation, we can use the <em>man</em> command and then provide the command we want to read the documentation for. Using our <em>ls</em> example, we would use <em>man ls</em> to view the manual pages for <em>ls</em>,
<img width="926" height="732" alt="image" src="https://github.com/user-attachments/assets/c157da32-bc21-4d96-81c6-0c5d3a528994" />




<img width="838" height="128" alt="image" src="https://github.com/user-attachments/assets/18fd08ea-e36c-46d0-b86c-fe87198871ae" />
<img width="921" height="610" alt="image" src="https://github.com/user-attachments/assets/b2aa196e-29dc-4dfc-8eb8-f2f195c4ce26" />






