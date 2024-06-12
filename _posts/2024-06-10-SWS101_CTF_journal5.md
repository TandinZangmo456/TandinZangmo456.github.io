---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal4]
Tags: [SWS101]
---

### Topic: startup
The command used is sudo nmap IP -vv the result is that we have 3 open ports details are 21, 22 and 80. Looking at the results from the nmap command that was issued with the IP, I got to know that ftp allows anonymous login. We have folder called ftp that has nothing and there are two other files important. jpg and notice. txt. In the text file, there is nothing of importance; also, I did try opening the jpg with steghide but it needs a password; binwalk has extracted a zlib file that I could not open. That is all right so let move to the next port which is number eighty that is port 80. 

At the level of the essence that generates the website, there is nothing interesting, whether in the code or on the home page. gobuster dir -w /usr/share/dirb/wordlists/common. txt -u http://IP -r we have a folder called /files. If we go there and look carefully, we will see that we maintain the same files that we had in the ftp server. Then copy a php shell to the ftp directory of the ftp server. Next, start a listener on our machine nc -nlvp 1234 and to spawn the shell just click on it from the browser. The shell will either return to normal or it means that we are being represented by another user www-data. python3 -c ‘import pty; pty. spawn(“/bin/bash”)’. 

The current directory we will be in is / and this should still be visible in the terminal. Scout around the directories we have with us now. There are some interesting ones such as: /incidents, /vagrant , and the file recipe I will briefly describe three new projects that are relevant to the virus’s ability to spread through networks of computer systems. txt. as answer for the first question it will be l*** where in the latter file it will be found. All that I see in /vagrant is boring, while in /incidents there is a . pcapng file called suspicious. pcapng that it is good to look into it. 

Transfer suspicious. wget the file pcapng to our system through nc and then launch it on our wireshark. From there right click any TCP packet and go to Follow->TCP stream. 
 
We have a communication between a server, or a web page and a particular client. Here it attempted a password for www-data but it still failed. This password is for sure left here for a purpose. 
go to directory home and if you type in the terminal you will see a user named lennie. perhaps the password is for lennie. su lennie then paste in the password and you are Lennie now. Copy the answer for the 2nd question which is user. txt ✨. 
It is noted that there is a folder called scripts. Within it you have a Script Planner. sh and a file stratrup_list. Most of these objects are URLs or links that connect to Web pages or some kind of online resources. txt owned by root, interesting!!! to say the least! cat planner. sh 
 
The role of this script is to print the value of LIST into startup_list. txt and then running of the script / etc/print. sh. ls -l /etc/print. sh 
 
It seems that we have the permissions for changing the print. sh file that user root execute it ‘This is due to the fact that the various scripts are stored in the “/root” directory. Judging from the way things are happening, it is evident that there is a cron job running planner. sh. 
 
 
Therefore, it must be altered to a form that can allow for the obtaining of the root. txt. echo ‘cp /root/root. txt /home/lennie/root. txt’ >> /etc/print. sh. Thus, root will execute planner of HDFS. le which will then execute a print. sh and we will get a file in the home directory of lennie called root. Txt containing the latest flag✨. Wait for some time may be a minute or so to get back the file.