# HTB_Blocky
My Blocky writeup!

👻 Blocky: A Haunting Minecraft Server Exploit
A Spooky Hack The Box Walkthrough

Machine Name: Blocky
Difficulty: Easy 👻
Author: Lantern
Date Compromised: April 2025

🌑 The Story: A Cursed Server
Deep within the digital graveyard of Hack The Box lies Blocky, a forsaken Minecraft server harboring dark secrets. The admin, a reckless soul, left behind a cursed JAR file containing the keys to the kingdom. Your mission? Unearth its horrors, breach the system, and escape before the server's ghosts trap you forever...

🔮 Attack Summary
1. Enumeration: The Ouija Board
Nmap Scan: Revealed open ports (21/FTP, 22/SSH, 80/HTTP, 25565/Minecraft).

![1 nmap](https://github.com/user-attachments/assets/a1604592-76ea-4f3f-8aec-90f85fb52774)


Web Server: A ghostly WordPress site redirected to blocky.htb.

Dirbuster: Uncovered a haunted /plugins/ directory with a possessed JAR file.

![2 jar file](https://github.com/user-attachments/assets/69db6f70-c1eb-46d7-9ddb-8a1a8613e729)


2. Exploitation: The Summoning Ritual
Decompiled BlockyCore.jar with JD-GUI, revealing a cursed password:


![3 decompile](https://github.com/user-attachments/assets/beb6d1bf-7557-4716-af46-1b335c4e231b)

```java
public String sqlPass = "8YsqfCTnsxAUeduz}NSXe22"; // The demon's whisper...
```

SSH Login: Used the password to possess the user notch (a nod to Minecraft’s creator).

![4 user flag](https://github.com/user-attachments/assets/c7bc7fed-1361-4e28-b14e-3f24ea92352a)


3. Privilege Escalation: The Possession
Sudo Spell: The password granted root access—a classic case of password reuse from beyond the grave.

```bash
sudo su  # The dead shall rise...
Password: 8YsqfCTnsxAUeduz}NSXe22
```

![5 root flag](https://github.com/user-attachments/assets/2893d472-19f7-45c0-9fc2-5581d26aefa8)


Flags Claimed:

User Flag: /home/notch/user.txt (A ghostly whisper).

Root Flag: /root/root.txt (The admin’s final scream).

💀 Lessons from the Crypt
Beware of Cursed Files: Exposed JARs/plugins can reveal passwords.

Password Reuse is a Death Curse: The same key unlocked SSH, MySQL, and sudo.

Sudo -l is a Séance: Always check for easy escalation paths.

🕯️ Commands Used (For the Brave)
bash
# 1. The Summoning (Nmap)  
nmap -p- -A -v 10.10.10.37  

# 2. The Séance (Decompile JAR)  
jd-gui BlockyCore.jar  

# 3. The Possession (SSH)  
ssh notch@blocky.htb  
Password: 8YsqfCTnsxAUeduz}NSXe22  

# 4. The Ascension (PrivEsc)  
sudo su  
cat /root/root.txt  # The final horror...
🔮 Final Words
Blocky serves as a chilling reminder of how simple missteps—like password reuse and exposed files—can haunt a system forever.

Rest in Pentest.

📜 License: MIT
👻 Author: Lantern


🎃 Happy Hacking—and Watch Your Back.
