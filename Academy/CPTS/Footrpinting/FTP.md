
- FTP -

Task 1:
<img width="1690" height="468" alt="image" src="https://github.com/user-attachments/assets/e8537a89-389f-47b8-8065-48c1c379685b" />

Ok, so as the first task we have to check which version of ftp server is running on the target, and we have to submit the banner as the answer. 

Supposedly, we could just use nmap for this task. 

<img width="1908" height="904" alt="image" src="https://github.com/user-attachments/assets/0358405e-a6c5-438e-97ba-cb1c98e3830e" />

From the screenshot we see several interesting things besides the answer. We see that the script scan has detected that anonymous login is allowed, it also shows the file that FTP server contains which might be come handy for the next task. 

nmap breakdown: 

sudo nmap -p21 -sC -A 10.129.67.59 \
-sC: Script scanning, uses scripts from NSE (Nmap Script Engine)\
-p21: Specifies the port and scans only this port which is FTP's default port\
-A: Aggressive scan, includes OS detection, version scan, traceroute and NSE execution 

<img width="1658" height="478" alt="image" src="https://github.com/user-attachments/assets/a2f6f72e-615b-4d0c-8d9e-c6c7aaf47d32" />


Task 2: 
<img width="1674" height="498" alt="image" src="https://github.com/user-attachments/assets/bcad792a-93c7-4ca6-adb9-9f79c48042cb" />

Here, we have 2 ways of downloading the file, first we can login as anonymous in FTP server, or we can just use wget to download the file. Lets use both ways

1: 
<img width="1082" height="602" alt="image" src="https://github.com/user-attachments/assets/dda874c5-2c51-497e-8394-7b4a95a62615" />
<img width="530" height="100" alt="image" src="https://github.com/user-attachments/assets/a79b4be8-8409-4607-9ede-f3d8d55e46dd" />

2: 
<img width="1904" height="1020" alt="image" src="https://github.com/user-attachments/assets/53921ca0-cfff-4b7e-a365-3921072b1a5f" />
<img width="658" height="182" alt="image" src="https://github.com/user-attachments/assets/d120f4f0-c520-44ab-ba4e-37e78ba5f6d3" />

So what is the difference between these two? \
Well, the GET method requires us to login insid the ftp ttl, and we can selectively download the files. On the other hand the wget method allows us to login right away, we just have to specify the login and password in the command, and contrary to the first method, the wget downloads all the files that could be downloaded and also saves them under a directory which is named after the IP address of the service.


<img width="1668" height="462" alt="image" src="https://github.com/user-attachments/assets/1e6d5c56-6819-4ba8-9ace-a5a1acae08f6" />
