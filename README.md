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
![Assets discovery](images/find assets.png)

### Assets page
![Assets page listing](images/assets.png)

### robots.txt (password found)
![robots.txt shows password](images/robot.txt.png)

### How I found the login page
![How I found login page](images/how i found login page.png)

### Login / home page
![Login & home page](images/login home page.png)

### Portal — `ls` output (first view)
![Portal listing - first step](images/ls in portal first step.png)

### File discovered: Sup3rS3cretPickl3Ingred.txt
![Portal listing - first step](images/ls in portal first step.png)

### Ingredient 1 — contents of Sup3rS3cretPickl3Ingred.txt
![First ingredient: mr. meeseek hair](images/first page.png)

### Check /home
![sudo ls /home](images/sudo ls home.png)

### /home/rick contents
![sudo ls /home/rick](images/sudo ls home rick.png)

### Ingredient 2 — second ingredients file
![Second ingredient: 1 jerry tear](images/third ingrd.png)

### whoami (www-data)
![whoami shows www-data](images/whoami www data.png)

### sudo -l (shows NOPASSWD: ALL)
![sudo -l shows NOPASSWD: ALL](images/sudo ls www data.png)

### Root folder listing
![sudo ls -la /root](images/sudo ls root.png)

### Ingredient 3 — /root/3rd.txt
![Third ingredient: fleeb juice](images/third ingrd.png)

---
