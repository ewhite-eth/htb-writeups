
FTP

<img width="1690" height="468" alt="image" src="https://github.com/user-attachments/assets/e8537a89-389f-47b8-8065-48c1c379685b" />

Ok, so as the first task we have to check which version of ftp server is running on the target, and we have to submit the banner as the answer. 

Supposedly, we could just use nmap for this task. 

<img width="1908" height="904" alt="image" src="https://github.com/user-attachments/assets/0358405e-a6c5-438e-97ba-cb1c98e3830e" />

nmap breakdown: 

sudo nmap -p21 -sC -A 10.129.67.59 /
-sC: Script scanning, uses scripts from NSE (Nmap Script Engine)
-p21: Specifies the port and scans only this port which is FTP's default port
-A: Aggressive scan, includes OS detection, version scan, traceroute and NSE execution



