---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal9]
Tags: [SWS101]
---

### Topic: Hydra

Task-1 Hydra Introduction 
 
Today, I proceeded with my investigation of specific tools used by hackers and geeks; thus, I came across Hydra, which is suitable for the password brute-forcing. Hydra can be useful when it comes to typing several passwords on the page of authorization or on the SSH server and, therefore, it is an indiscreet tool in the sphere of Security Penetration Testing. 
 
Task-2 Using Hydra 
 
As for the first task, I had to apply Hydra and search for Molly’s web password finding it through brute force attack. The command I used was:The command that I entered was: 

hydra -l molly -P rockyou.txt http-post-form "/login:username=^USER^&password=^PASS^:incorrect" -V
 
This command tunes the username as “molly”, uses the rockyou password list, and runs with verbose mode, and maximum thread count. In Targeted and Uncovered Data, the wordlist of 5000 txt words is used for password guessing and it attacks the form “/login” of the web server. After running the command, I obtained Flag 1:When the command was entered I acomplished the following as well as received Flag 1. 
 
Flag 1: THM{2673a7dd116de68e85c48ec0b1f2612e} 
 
In the second task I succeeded to pass Hydra which allows me guess correctly Molly’s SSH password. The command I used was:The command that I issued was:

hydra -l molly -P rockyou.txt ssh -V
 
This command sets the value of the username as ‘molly’ and the password as ‘rockyou’ word list and lastly, it puts the scanner mode to passive. txt wordlist for password guesses, and is still targeting SSH for brute force. After running the command, I discovered Molly's SSH password and logged in using:So, I used the fhunter command to find the SSH password for Molly and logged in with that.

ssh molly@IP
 
Last of all, the user creates a new directory with an identified name and logs in as root, follows the new created directory, and by applying the command ‘cat’, the user reads the content of the file containing the flag. The flag was: 
 
Flag 2: THM{c8eeb0468febbadea859baeb33b2541b} 
 
All these tasks were a good overall to Hydra and to its efficiency in password brute-forcing. I would also like to elaborate on the other aspects that will be enabled by the use of Hydra, or as a case discover how the current use could be enhanced.