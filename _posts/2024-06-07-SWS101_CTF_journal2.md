---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal2]
Tags: [SWS101]
---

### Topic: Bounty Hacker

Finding the open ports.

First i will do a Nmap Scan:
While doing a nmap scan on the target IP(10.10.4.122), we will know what ports running on the target IP.

We get to know that there are 3 ports open on the box:
1. 21/ftp- vsftpd 3.0.3 (Anonymous FTP login allowed)
2. 22/ssh- OpenSSH 7.2p2
3. 80/http- Apache/2.4.18

Answer the questions below
Who wrote the task list?
Answer : lin

What service can you bruteforce with the text file found?
Answer: ssh

What is the users password?
Answer: RedDr4gonSynd1cat3

user.txt
Answer: THM{CR1M3_SyNd1C4T3}

root.txt
Answer: THM{80UN7Y_h4cK3r}

Looking at the source code of the page, no distinctive information could be identified. Here I could also start the gobuster and list out for example the folders and files which are accessible with the webserver. Furthermore, the image could be retrieved and scraped just to decipher if there is a hidden message into this. But like there is an FTP server running there that has the feature of anonymous login, so let us begin with the FTP server first. In the worst-case scenario, we go back to the web server level where we started at the beginning of the former loop. 
 
But first, as there are some usernames popping out it looks like. We have to take a step and save those we can. we may never be sure if they are indeed real users accounts. Well, I made a file still named usernames. txt and stored these names on the different lined. Can be useful if we have to try or crack something as in the case of bruteforcing a network for example. Choose any text editor of your preference nano, vim, emacs . . . But we are not gong for another stupid editor war. so I depicted another way round this. 

This variable involves actually getting connected to the FTP server and start browsing through it.
Logging into the FTP Server:Logging into the FTP Server:

Since it did not require any particular identifier to login, I logged in via the FTP anonymous login.
Connected ‘rcx.exe’ to a terminal and set the current directory on my machine to an appropriate path for cloning files to.
 
**Server Connection and Navigation:**
Established to the server at IP 10. 10. 23. 89 which has vsFTPd 3. 0. 3.
Logged in using anonymous as the username.

**Listing and Downloading Files:**
Check the FTP server and noticed files that have locks on them. txt and task. txt. txt.
I copied these files to my local computer.

**Analyzing Downloaded Files:**
locks. It stated that the possible password was a list of strings was stored in the passwd|loc txt.
task. txt was filled with hints about usernames; the phrases were “Protect Vicious” and “Pick-up Red Eye on the moon”.

Using 
$ cat locks.txt 
rEddrAGON
ReDdr4g0nSynd!cat3
...
$ cat task.txt 
1.) Protect Vicious.
2.) Plan for Red Eye pickup on the moon.
-lin
we get the answer.

**While carrying out the brute force attack the following should be done:**
**Setting Up Usernames List:**
Listed potential usernames extracted from the given task are as follows. txt and get the usernames consisting of “vicious” and “lin”. txt.

**Brute Forcing with Hydra:**
Appealed to Hydra in order to perform an ssh login with the obtained usernames and passwords.

Using this command
hydra -t 16 -L usernames.txt -P locks.txt $IP ssh

Successfully found the SSH credentials: login: lin, password: ReDdr4g0nSynd1cat3.
To third, connecting to the SSH Server when logging in.

**SSH Login:**
Connected to the location of the video on the SSH server with the received-login information.
ssh lin@10.10.23.89

**Exploring the System:**
He straight away changed the directory to the ~/Desktop of a user. which was indicated to be txt was searched and its content read.

Using this command we get this answer
lin@bountyhacker:~/Desktop$ cat user.txt 
THM{CR1M3_SyNd1C4T3}

Looked into other directories which included Documents, Music, Pictures, and so on; However, I did not come across anything substantial.

Privilege Escalation
Checking Sudo Permissions:
Examined what lin can execute with the help of sudo and realized that the user can execute tar with root permission.

Exploiting Sudo Tar:
A known sudo tar exploitation was used to obtain a root shell.
Obtained the root access and read the root flag.

(# whoami)
root
(# cat /root/root.txt)
THM{8***7Y_h4***r}
