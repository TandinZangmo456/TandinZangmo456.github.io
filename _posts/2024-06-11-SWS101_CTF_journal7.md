---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal7]
Tags: [SWS101]
---

### Topic:bsidesgtthompson

Overview 
This room focuses on the Thompson’s TryHackMe platform along with the pragmatic approaches used in cybersecurity, and more specifically in the Capture the Flag (CTF) kind. At the end of this report I am going to explain stage by stage how I managed to look for this flag in this room. 
 
Objectives 
Basics of the allocated BSidesGTThompson room, its layout, and purposes. 
Integrate numerous type of cybersecurity measure and strategies. 
These are ways in which one can successfully find the flag, and capture it. 

Methodology 
1. Initial Reconnaissance 
The first process links the identification of information sources to the target. This is carried out by a series of reconnaissance tools such as scanning for opened ports, services running and other possible paths. 
 
Tools Used: 
Nmap: An application for the discovery of hosts and services on a computer network sometimes used in penetration testing. 

nmap -sC -sV -oN initial_scan.txt <10.10.241.108>

 
Service Enumeration 
 
Subsequently, due to the results gathered from the initial sweeping, detailed probing of particular services is performed. This means that you are to determine version numbers, configurations and possible risks. 
 
Steps: 
Perform a web service scan by opening a web browser to check HTTP/HTTPS services. 
List down the services namely FTP, SSH, and others services that have been discovered. 
 
3. Vulnerability Analysis 
 
In the next operation that follows the enumeration phase, the analyst is expected to search for any known exploits of the services that are operational on the target system. 
 
Tools Used:  
Searchsploit: It is a basic command-line tool to search exploit in Exploit-DB. 
Nessus: A vulnerability scanner 
 
4. Exploitation 
 
After discovering the weaknesses, the method that follows involves taking advantage of those weaknesses with the intention of attaining entry into the target system. This may require the use of known public exploits or a script of the researcher’s own design. 
 
Example: 
 
Taking advantage of an old WordPress plugin. 
 
Metasploit Framework with the help of which the process of exploitation is semi-automated.

msfconsole
use exploit/multi/http/...
set RHOST <target_IP>
run

5. Privilege Escalation 
The second goal is achieved after getting a foothold, the next step is to acquire more permissions on the target system. This often involves the searches for one or many misconfigurations or other secondary vulnerabilities in the system. 
 
Techniques: 
Sudo misconfigurations: Looking for commands that call can be run with root privilege level, without having to type in the password. 
Kernel exploits: Exploiting vulnerabilities specific to a particular operating system or Windows/ DOS version. 

6. Capture the Flag 
The last step is always to find the flag that was planted at the starting line once the root or administrative access has been gained. The flag is normally kept in the system in a given file commonly in root directory or any other secure directory. 
 
Conclusion 
The method of searching for the flag in the environment of the room named ‘ BSidesGTThompson’ presupposes performing a number of steps: reconnaissance, enumeration, vulnerability analysis, exploitation, privilege escalation. The later steps utilise the results of the preceding steps, and the goal in mind is used to get closer to the discovery. This exercise is useful in achieving the course objective of understand simple punitive measures in cybersecurity and refining problem solving skills in actuality. 
 
Key Takeaways 
Necessity of detailed intelligence and identification. 
Effective targeting or putting into practice what in military strategy is called ‘search, find, fix and strike. ’ 
Promoting privileges to the highest level to have complete access on the target system. 
Indeed, one of the major aspects of CTF is regularity and patience in solving given tasks. 
Widely chunked to this report is a step by step structural attack plan that was used to solve the BSidesGTThompson room on TryHackMe and should help to build enhanced understanding of the processes and methodologies that were used to capture the flag. 
 
