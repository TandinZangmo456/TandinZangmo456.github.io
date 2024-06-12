---
Title: SWS101 CTF 
Categories: [SWS101, CTFJournal1]
Tags: [SWS101]
---

### Topic: Crack the Hash 

**Task 1 : Level 1**

Can you complete the level 1 tasks by cracking the hashes?
1. MD5 Hash
*Hash* : 48bb6e862e54f2a795ffc4e541caed4d
    In this first hash, it gives us hint like MD5 which means that it is a MD5 hash. To crack this hash we use command like 'hashcat -m 0 hash1_1.txt /usr/share/wordlists/rockyou.txt --show'

    The password shown is "easy"

2. SHA1 Hash
*Hash* : CBFDAC6008F9CAB4083784CBD1874F76618D2A97  
    In this second hash, it provide us with hint as Hashcat supports many SHA TYPES. So we use "hashcat -m 100 hash1_2.txt /usr/share/wordlists/rockyou.txt --show" command line to get the password.

    The  password shown is "password123"

3. SHA256 Hash
*Hash* : 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032
    In this third hash, we get to know that this is s SHA hash as the hint for this particular work. so to get the password we use 'ashcat -m 1400 hash1_3.txt /usr/share/wordlists/rockyou.txt --show' to get the password.

    The password achieved is "letmein"

4. bcrypt Hash
*Hash* : $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom
    In this fourth hash, we get to know that it gives us hint as bcrypt hash so with the command 'hashcat -m 3200 hash1_4.txt /usr/share/wordlists/rockyou.txt' we can get the password.

    The Password is "bleh"

5. MD4 Hash
*Hash* : hashcat -m 900 hash1_5.txt /usr/share/wordlists/rockyou.txt
    In this the hint says that this is MD4 hash so when i use this command 'hashcat -m 900 hash1_5.txt /usr/share/wordlists/rockyou.txt' it didn't give us anything so using this online tool https://md5decrypt.net/en/Md4/ we got the password.

**Task 2 : level 2**

Crack more complex hashes using hashcat.
1. SHA256 Hash
*Hash* : F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85
    with this command line 'hashcat -m 1400 hash2_1.txt /usr/share/wordlists/rockyou.txt' we get the password. 

    The password is "paule"

2. NTLM Hash
*Hash* : 1DFECA0C002AE40B8619ECF94819CC1B
    Hint: This is an NTLM hash.

    Command Used: hashcat -m 1000 hash2_2.txt /usr/share/wordlists/rockyou.txt

    The password we got is "n63umy8lkf4i"

3.  SHA-512 (Unix) Hash
*Hash*: 
    Command Used: hashcat -m 1800 hash2_3.txt /usr/share/wordlists/rockyou.txt

    The password is "waka99"

4. HMAC-SHA1 Hash
*Hash* : e5d8870e5bdd26602cab8dbe07a942c8669e56d6
    Hint : This is a HMAC-SHA1 hash.
    Command Used: hashcat -m 160 hash2_4.txt /usr/share/wordlists/rockyou.txt

    The password is "481616481616"

In both tasks, we are provided with various distinct types of hashed passwords. Essentially, with the help of hashcat – a powerful tool for password cracking, we proceed to match these hashes with a standard ‘password’ list, namely rockyou. txt. Depending on the sort of hash (MD5, SHA1, SHA256, bcrypt, etc. ), we employ certain modes in hashcat to accomplish the objective of decoding or identifying the original passwords. After failing to work with hashcat, there is an option for online tools to help in cracking.