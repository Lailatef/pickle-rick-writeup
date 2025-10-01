# Pickle Rick Potion — TryHackMe Writeup

**Author:** Laila  
**Target IP:** 10.10.233.152  
**Date:** 2025-09-30

This repository contains my writeup and evidence for the "Pickle Rick" TryHackMe room — a web CTF where I enumerated a web app, authenticated to a portal, and escalated to root to retrieve three secret ingredients.

---

## Quick summary
**Recovered ingredients**
1. `mr. meeseek hair`  
2. `1 jerry tear`  
3. `fleeb juice`

---

## Evidence / Screenshots

### Nmap scan
![Nmap scan output](screenShots/nmap.png)

### Gobuster / assets discovered
![Assets listing](screenShots/find assets.png)

### Assets page 
![Assets listing](screenShots/assets.png)

### robots.txt (password found)
![robots.txt shows password](screenShots/robot_txt.png)

### How I found the login page
![How I found login page](screenShots/how_i_found_login_page.png)

### Login / home page
![Login & home page](screenShots/login_home_page.png)

### Portal — `ls` output (first view)
![Portal listing - first step](screenShots/ls_in_portal_first_step.png)

### File discovered: Sup3rS3cretPickl3Ingred.txt
![Sup3r file in portal](screenShots/ls_in_portal_first_step.png)

### Ingredient 1 — contents of Sup3rS3cretPickl3Ingred.txt
![First ingredient (mr. meeseek hair)](screenShots/first_page.png)

### Check /home
![sudo ls /home](screenShots/sudo_ls_home.png)

### /home/rick contents
![sudo ls /home/rick](screenShots/sudo_ls_home_rick.png)

### Ingredient 2 — second ingredients file
![Second ingredient (1 jerry tear)](screenShots/third_ingrd.png)

### whoami (www-data)
![whoami shows www-data](screenShots/whoami_www_data.png)

### sudo -l (shows NOPASSWD ALL)
![sudo -l shows NOPASSWD: ALL](screenShots/sudo_ls_www_data.png)

### Root folder listing
![sudo ls -la /root](screenShots/sudo_ls_root.png)

### Ingredient 3 — /root/3rd.txt
![Third ingredient (fleeb juice)](screenShots/third_ingrd.png)

---
