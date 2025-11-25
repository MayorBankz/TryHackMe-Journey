# TryHackMe - Linux Fundamentals Part 3
* Date: 21-11-25
* Level: Beginner

## Linux Fundamentals (Part 3)
## Introducing terminal text editors
1. Nano - To create or edit a file using nano, we simply use <em><i>nano filename</i></em> -- replacing "filename" with the name of the file you wish to edit.
Nano has a new features that are easy to remember & covers the most general things you would want out of a text editor, including:
* Searching for text
* Copying and pasting
* Jumping to a line number
* Finding out what line number you are on

You can use these features of nano by pressing the "Ctrl" key (which is represented as an <em>^</em> on linux) and a corresponding letter. For example, to exit, we would want to press <em>"Ctrl"</em> and "X" to exit Nano.

2. VIM
Vim is a much more advanced text editor. Some of VIM's benefits, albeit taking a much time longer time to become familiar with, includes:
* Customisable - you can modify the keyboard shortcuts to be your choosing.
* Syntax Highlighting - this is useful if you are writing or maintaining code, making it a popular choice for software developers.
* VIM works on all terminals where nano may not be installed
* There are a lot of resources such as cheatsheets, tutorials and the sorts available to use

## General/Useful Utilities
Downloading Files
* <em>wget</em> - This command allows us to download files from the web via HTTP --as if you were accessing the file in your browser. We simply need to provide the address of the resource that we wish to download. For example, if I wanted to download a file named
"myfile.txt" onto my machine, assuming I knew the web address -- it would look something look like this
<span style="color:blue"><em><i>wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.tx</i></em></span>

## Transferring Files From Your Host - SCP (SSH)
Secure copy, or SCP, is just that--a means of securely copying files. Unlike the regular cp command, this command allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption.
Working on a model of SOURCE and DESTINATION, SCP allows you to:
* Copy files & directories from your current system to a remote system
* Copy files & directories from a remote system to your current system.
Provided that we know usernames and passwords for a user on your current system and a user on the remote system. For example, let's copy an example file from our machine, which I have neatly laid out in the table below:

| Variable | Value |
| -------- | ------ |
| The IP address of the remote system | 192.168.1.30 |
| User on the remote system | ubuntu |
| Name of the file on the local system | Important.txt |
| Name that we wish to store the file as on the remote system | transferred.txt |

With this information, let's craft our <em><i>scp</i></em> command (remembering that the fromat of SCP is just SOURCE and DESTINATION)

<span style="color:blue"><em><i>SCP important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt</i></em></span>

And now let's reverse this and layout the syntax for using <em><i>scp</i></em> to copy a file from a remote computer that we're not logged into

| Variable |
| -------- |
| IP address of the remote systme |
| User on the remote system |
| Name of the file on the remote system |
| Name that we wish to store the file as on our system |
| Name that we wish to store the file as on our system |

The command will now look like the following: <span style="color:blue"><em>scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt</em></span>

## Serving Files From Your Host - WEB
Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use model called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded
by another computing using commands such as <em><i>curl</i></em> and <em><i>wget.</i></em>.
Python3's "HTTPServer" will serve the files in the directory that you run the command, but this can be changed by providing options that can be found in the manual pages. Simply, all we need to do is run.
<em><i>python3 -m http.server</i></em> to start the module. In the example provided below, we are serving from a directory called "webserver", which has a single named "file".

<em>cmnatic@CMNatic-THM-LPTOP: ~/webserver</em>
<em>cmnatic@CMNatic-THM-LPTOP:~webserver$</em> </i>ls<i/>
file
<em>cmnatic@CMNatic-THM-LPTOP:~webserver$</em> <i>python -m http.server</i>
serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8000/)

## Processes 101
Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. 

## Viewing Processes
We can use the friendly <em><i>ps</i></em> command to provide a list of the running processes as our user's session and some additional information such as its status code, the session that is running it, how much usage
time of the CPU it is using, and the name of the actual program or command that is being executed.

To see the processes run by other users and those that don't run from a session (i.e. system processes), we need to provide <i>aux</i> to the <i>ps</i> command.

Another very useful command is the top command; top gives you real-time statistics about the processes running on your system instead of a one-time view. These statistics will refresh every 10 seconds, but will also refresh
when you use the arrow keys to browse the various rows. Another great command to gain insight into your system is via the <em><i>top</i></em> command.

## Managing Processes 
You can send signals that can terminate processes; there are a variety of types of signals that correlate to exactly how "cleanly" the process is dealt with by the kernel. To kill a command, we can use the appropriately named <em><li>kill</li></em> command and the associated PID that we wish to kill. i.e., to kill PID 1337, we'd use <em><i>kill 1337</i></em>
Below are some of the signals that we can send to a process when it is killed:
* SIGTERM - kill the process, but allow it to do some cleanup tasks beforehand
* SIGKILL - Kill the process - doesn't do any cleanup after the fact
* SIGSTOP - Stop/suspend a process

## Maintaining Your System: Automation
Users may want to schedule a certain action or tasks to take place after the system has booted. Take for example, running commands, backing up files, or launching your favorite programs on, such as Spotify or Google Chrome. 

Crontab is one of the process that is started during boot, which is responsible for facilitating and managing cron jobs.
A crontab is simply a special file with formatting that is recognised by the <em><i>cron</i></em> process to execute each line step-by-step. Crontabs require 6 specific values:

| Value | Description |
| ----- | ----------- |
| Min | What minute to execute it |
| Hour | What hour to execute at  |
| DOM | What day of the month to execute at |
| MON | What month of the year to execute at |
| DOW | Day of the week to execute at |
| CMD | The actual command that will be executed |

## Maintaining Your System: Package Management
Introducing Packages & Software Repos
When developers wish to submit software to the community, they will submit it to an "apt" repository. If approved, their programs and tools will be released to the wild. Two of the most redeeming features of Linux shine to light here: User accessibility and the merit of open source tools.

## Managing Your Repositories (Adding & Removing)
Normally, we use the apt command to install software onto our ubuntu system. The <em><i>apt</i></em> command is part of the package management software also named apt. Apt contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove software at the same time.

## Maintaining Your System: Logs
* Located in the /var/log directory
* These files and folders contain logging information for applications and services running on your system.
* The Operating System (OS) has become pretty good at automatically managing 

## Lab (Nano)
<img width="833" height="711" alt="image" src="https://github.com/user-attachments/assets/7f02a2c8-d9d1-4f9e-89db-fff3e312e9ac" />

## Lab ( Crontab)
Let's use the example of backing up files. You may wish to backup "Mayowa"'s "Documents" every 12 hours. We would use the following formatting:
<em><i>0 *12 * * * cp -R /home/mayowa/documents /var/backups/</i></em>

An interesting feature of crontabs is that these also support the wildcard for asterisk ( * ). If we do not provide a value for that specific field, i.e. we don't care what month, day, or year it is executed -- only that 
it is executed every 12 hours, we simply just place an asterisk.
This can be confusing to begin with, which is why there are some great resources such as the online "Crontab Generator" that allows you to use a friendly application to generate your formatting for you! As well as the site "Cron Guru"!

Crontabs can be edited using <em><i>crontab -e</i></em>, where you can select an editor (such as Nano).

<img width="939" height="492" alt="image" src="https://github.com/user-attachments/assets/f92a47c6-13fd-49a2-89fe-288cc412d362" />

## Lab (apt) - Adding and Removing (Cisco Cybersecurity LabVM)
Let's walk through adding and removing a repository using the <em><i>add-apt-repository</i></em> command. While you can install software through the use of package installers such as <em><i>dpkg</i></em>, the benefits of apt means that whenever we update our system -- the repository that contains the pieces of software that we add also gets checked for updates. 
In this example, we're going to add the text editor <em>Sublime Text</em> to our ubuntu machine as a repository as it is not part of the default ubuntu repositories. When adding software, the integrity of what we download is guaranteed by the use of what is called GPU (Gnu Privacy Guard) keys. These keys are essentially a safety check from the developers saying, "here's our software". If the keys do not match up to what your system trusts and what the developers used, then the software will not be downloaded.

* Procedures
So, to start, we need to add the GPG key for the developers of the Sublime Text 3.

1. Let's download the GPG key and use apt-key to trust it
* <em><i>wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -</i></em>
2. Now that we have added this key to our trusted list, we can now add Sublime Text 3's repository to our apt sources list. We can now add Sublime Text 3's repository to our apt sources list. A good practice is to have a separate file for every different community/3rd party repository that we add
Let's create a file named sublime-text.list in /etc/apt/sources.list.d and enter the repository information like so:
* <em>root@linux3:/etc/apt/sources.list.d# <i>touch sublime-text.list</i></em>
* <em>root@linux3:/etc/apt/sources.list.d# <i>ls</i></em>
* <em>root@linux3:/etc/apt/sources.list.d# 🟨</em>

3. And now use Nano or a text editor of your choice to add & save the Sublime Text 3 repository into this newly created file:
* <em><i>deb https://download.sublimetext.com/ apt/stable/
* 🟨
4. After we have added this entry, we need to update apt to recognise this new entry -- this is done using the <em><i>apt update</i></em> command
5. Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using <em><i>apt install sublime-text</i></em>
Removing packages is as easy as reversing. This process is done by using the <em><i>add-apt-repository --remove ppa:PPA_Name/ppa</i></em> or by manually deleting the file that we previously fulfilled. Once removed we can just use <em><i>apt remove [software-name-here] i.e. apt remove subime-text</i></em>
