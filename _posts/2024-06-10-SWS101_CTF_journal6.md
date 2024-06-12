---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal6]
Tags: [SWS101]
---

### Topic:DAV

The challenge I will solve today is called Dav and 2 flags must be found in order to complete it: user\_flag and root\_flag The two flags include the very important user flag and the root flag.

Upon booting up, the first action I took was performing an IP scan of the IP issued by TryHackMe. It is important to note that the first scan was done with nmap. Actually it is presented in the result below where we have identified port 80 being opened and the service that is running at this port is Apache server.


NMAP Scan
Indeed when I went to the page I found it rather boring or useless since it is the Apache default page. Oh no I looked at the source code to see whether I could find anything then there was nothing. The next process was to initiate a scan with gobuster that targets other possible paths that can be accessed. I used small. As for the HTML scans, it only gave one result which I inputted from the txt file for this scan.


sh. Gobuster Scan
Following the link to which I have been directed by that recently discovered link, I was redirected to the login page. Though I did not uncovered any credentials up to that time, I used the clear Default password and tried SQL Injection but it failed. Then we were looking for the default login credentials of what I was previously looking for and, after some time, we managed to find out the default login username and password as well as how to upload files to the web server.

This rang the bell and I thought there is a chance and an opportunity to use a reverse shell. Finally, I attempted to login on the server through using the cadaver tool and the account details that I had discovered and I was so much delighted to note that I was indeed able to log in. Furthermore, I uploaded a PHP reverse shell.

Cadaver Login 
I decided to start netcat on port 1234 in the new terminal, so that I can connect with the PHP reverse shell I used where I set 1234 port and checked the file I just uploaded, and boom got a reverse shell with www-data user. 
 
 
Reverse Shell 
I went in directory /home to confirm what users are there, I met 2 users. User flag was discovered in the home directory of the 1 of these 2 users. I attempted to read the file, it let me! 
 
 
User Flag 
I believed that before root traversal I had to think about horizontal movement, but I decided to check whether www-data has sudo (to be honest, I did not have great expectations). After passing the check and realizing that this one does not require any input and, I have sudo rights to run /bin/cat, I understood that this one is done. I just ran 
 
sudo /bin/cat /root/root. txt because, as a rule, root flag is located in the root directory of the established shells, in /root path. And there it was!