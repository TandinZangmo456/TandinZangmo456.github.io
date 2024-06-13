---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal8]
Tags: [SWS101]
---

### Topic:wgelctf

Overview 
 The WGEL CTF room on TryHackMe is intended to improve participants’ abilities in cybersecurity to solve problems practically. It indicates how it is possible to search for this flag within this particular room following the described structural plan. 
 
 Objectives 
 Ten understand the structure and overall objective of the WGEL CTF room. 
 Implement the best practices of cybersecurity guidelines and measures. 
 Simply put find the flag and capture or reach it. 
 
 Methodology 
 1. Initial Reconnaissance 
 The first step is to conduct a survey that entails information related to the target machine. This entails a process of sweeping that brings out the open ports in the network and services running on the target. 
 
 Tools Used: 
 Nmap: Host discover tool used to scan the network. 
 
 2. Service Enumeration 
 As a next step after the activated Nmap scan, there is a detailed enumeration of the discovered services. This step is useful in identifying the various services that need to be delivered and finding out service interfaces. 
 
 Steps: 
 Implemented to search the HTTP/HTTPS services for available Web pages. 
 List the service following the observed scan including, FTP, SSH and otherwise. 

 3. Web Application Analysis 
 Whether a web service is found running or not, scanning the web application has to be performed. This includes gross examination by clinicians and limb amputation followed by X-ray scanning. 
 
 Tools Used: 
 Gobuster/Dirb: Programs to search for the hidden files and directories by simply attempting to guess the login name and password. 
 Nikto: Web server scanner to detect the known vulnerabilities. 
 
 4. Vulnerability Analysis 
 Employing the collected intelligence, it is possible to define any recognized weakness relevant to the services and/or applications functioning on the target host. 
 
 Tools Used: 
 Searchsploit: For searching known exploits Hence, it requires the use of Exploit-DB. 
 Nessus/OpenVAS: Penetration tools to check for possible areas in the applications that can be exploited. 
 5. Exploitation 
 The former of the two is to follow the discovered vulnerabilities to gain an entry into the system by taking advantage of them. That might include employing readily available exploits or programming their own scripts. 
 
 Example Exploitation: 
 Vulnerability in applications which are associated with the web or some of the services that are configured in a wrong way. 
 Exploitation through Metasploit Framework Again. 
 
 6. Post-Exploitation and Privilege Escalation 
 Once the attacker has initially compromised a system, he will want to move further and gain root or administrator permissions. This can include searching for one or more further weaknesses or misconfigurations that can be targeted. 
 
 Techniques: 
 Sudo misconfigurations: Search available commands able to be run by the root. 
 Kernel exploits: The advantage of the privilege escalation is some of the exploits are localized. 
 7. Capture the Flag 
 After getting root or administrative access kindly search for the flag file in the system. Flags are usually located at a certain part of kingdom, usually in the home directory of the root user. 
 
 cat /root/flag. txt 

 Conclusion 
 For flag that is located in the WGEL CTF room then it will go like Reconnaissance, service enumeration, Web application analysis, Vulnerabilities analysis, exploitation, post exploitation ad lastly privilege escalation in order to capture the flag. This challenge is useful in developing practical skills in cybersecurity to notice the application of certain tools and strategies. 
 
 Key Takeaways 
 High value of activities aimed at the detailed study of the environment and identification of services. 
 Extent to which Web Application analysis is efficient in determining risks. 
 Appliance of known exploit and custom script on the target system as a part of successful exploitation. 
 Back to normal system escalation of privileges to obtain the root access. 
 It is all about consistently and systematically working it out as they are designed with such parameters that requires longer time to solve. 
 This paper describes step and methodologies to solve the WGEL CTF room on TryHackMe and how to capture the flag.