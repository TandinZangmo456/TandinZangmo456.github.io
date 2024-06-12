---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal3]
Tags: [SWS101]
---

### Topic:picklerick

**Introduction**
Today I started the “PickleRick” Capture the Flag (CTF) room on TryHackMe. This CTF is based on the famous show Rick and Morty and consists of levels related to basic web exploitation and privilege escalation. The main task is to locate three flags that are dispersed between different sections of the system.

Initial Setup and Scanning
Connecting to the Target Machine:Connecting to the Target Machine:

I began by properly installing the machine, and recorded the IP assigned to it.
To begin, the initial reconnaissance step was performed by doing an Nmap scan in order to determine the opened ports and available services.

we used 
nmap -sC -sV -oN nmap_initial.txt <10.10.7.207>

Nmap Scan Results:
The scan revealed the following:
Port 22: SSH
Port 80: HTTP (Apache server)

Accessing the Web Server:
Opened web server in a browser and entered in the address line <10.10.7.207>.
Went to a simple webpage with references to Pickle Rick, but not much that could be helpful right away.

Directory Brute Forcing:
Selected gobuster to perform directory and file brute force.
we used : 
gobuster dir -u http://<10.10.7.207> -w /usr/share/wordlists/dirb/common.txt -o gobuster_results.txt

Gobuster Findings:
Found several directories, among them there were assets and the login directory. php, and /robots. txt. php. txt.

Reviewing Robots. txt:
Checked /robots. txt and found out that it was prohibited /portal. php.
Exploiting Web Vulnerabilities

Accessing Portal. php:
Navigated to /portal. php and got a login page.

Bypassing Login:
I tried the previous credential options but were not successful.
Moved on to look at the page source hoping to come across something that might be a credential or could lead to a credential.

Exploring Source Code:
From the source code found a string comment with the username and password to the portal

we found 
<!-- Username: R1ckRul3s Password: WubbaLubbaDubDub -->


Logging into Portal:
Authurized /portal with the credentials. php.
Finding the First Flag

Portal Access:
Got the executive access to the server and reached the root level panel where commands could be typed in without any restrictions.

Listing Files:
Utilized the command panel to categorize files by their directory; the home directory in particular.

First Flag:
Searched for the first flag file named Sup3rS3cretPickl3Ingred. txt.

We used 
cat /home/rick/Sup3rS3cretPickl3Ingred.txt
The content revealed the first ingredient: >”Mr. Meeseeks hair. “

Discovering the Second Flag
Exploring Further:

Carrying on with the file system and user directories investigation and analysis.
Another memo also indicates that the next cooking ingredient is in /home/rick

Finding the Second Flag:

It locates the second flag file named clue. txt in the same directory” should be translated to “The formula for calculating contig density and assembling the contigs into scaffolds will be written into a file named SeqAssembly.txt within the same directory.

cat /home/rick/clue.txt

with the help of this command  we get the second flag.
The content revealed the second ingredient: >1 Large American beer or 1 jerry tear.

Privilege Escalation

Checking Sudo Permissions:
Reviewed what commands the user was allowed to input with sudo.

Discovering a Vulnerability:
Discovered that the user could use sudo on all commands that require a password to type no password.
Implemented this to get the root access privilege.

Accessing Root Directory:
Moving to the root directory to get the ultimate flag.

Third Flag:
txt. php. Located 3rd. txt.
cat /root/3rd.txt

The content revealed the third ingredient: The Ndruyu language still to be seen in Ngindo today contains such heraldic terms as “fleeb juice. "

Conclusion

The today’s task was a thrilling adventure to the world of Pickle Rick, at least this is how it felt to me. Enumerating all the users details next, exploiting into admin account, and finally ‘becoming root,’ I was able to obtain all three flags. I really enjoyed this exercise because it helped me to practice the web exploitation techniques and gather the information about privilege escalation.

Key Learnings:
Significance of proper enumeration in infirmity of likely exploits.

Thus, applying the discovered credentials to successfully deceive security mechanisms or systems.

Using sudo privileges for acquiring additional privileges to root.



Flags Obtained:

Sup3rS3cretPickl3Ingred. txt: "mr. meeseeks hair"

clue. txt: "1 jerry tear"

3rd. txt: "fleeb juice"