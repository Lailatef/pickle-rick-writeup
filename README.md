# pickle-rick-writeup

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
![Nmap scan output](images/nmap.png)

### Gobuster / assets discovered
![Assets listing](images/find assets.png)

### Assets page 
![Assets listing](images/assets.png)

### robots.txt (password found)
![robots.txt shows password](images/robot_txt.png)

### How I found the login page
![How I found login page](images/how_i_found_login_page.png)

### Login / home page
![Login & home page](images/login_home_page.png)

### Portal — `ls` output (first view)
![Portal listing - first step](images/ls_in_portal_first_step.png)

### File discovered: Sup3rS3cretPickl3Ingred.txt
![Sup3r file in portal](images/ls_in_portal_first_step.png)

### Ingredient 1 — contents of Sup3rS3cretPickl3Ingred.txt
![First ingredient (mr. meeseek hair)](images/first_page.png)

### Check /home
![sudo ls /home](images/sudo_ls_home.png)

### /home/rick contents
![sudo ls /home/rick](images/sudo_ls_home_rick.png)

### Ingredient 2 — second ingredients file
![Second ingredient (1 jerry tear)](images/third_ingrd.png)

### whoami (www-data)
![whoami shows www-data](images/whoami_www_data.png)

### sudo -l (shows NOPASSWD ALL)
![sudo -l shows NOPASSWD: ALL](images/sudo_ls_www_data.png)

### Root folder listing
![sudo ls -la /root](images/sudo_ls_root.png)

### Ingredient 3 — /root/3rd.txt
![Third ingredient (fleeb juice)](images/third_ingrd.png)

---


