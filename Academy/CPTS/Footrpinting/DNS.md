# DNS

## 1st Task
<img width="1672" height="488" alt="image" src="https://github.com/user-attachments/assets/7264da4f-0a61-4bd7-bb89-1544a8dfc58f" />

This task basically asks us to find the domains FQDN (Fully Qualified Domain Name) its a complete and exact location in internet. 
How do we accomplish this? Well, just the use of dig command in combination with ns record and specifying the domain and ip should be pretty enough. 
<img width="1002" height="698" alt="image" src="https://github.com/user-attachments/assets/bbaccfb8-471e-4b90-a101-ac77c10940a0" />
```
dig ns inlanefreight.htb @10.129.79.122 
```

## 2nd Task
<img width="1666" height="522" alt="image" src="https://github.com/user-attachments/assets/eec3806c-abee-46d4-be83-64a5fa12d5a1" />

We have to find out if its possible to do some zone transferring. We can do this by using ```axfr``` option
<img width="1594" height="594" alt="image" src="https://github.com/user-attachments/assets/180d9473-531d-47d6-96b1-440065ac6766" />
as we can see, we found several records
app.inlanefreight.htb.
dev.inlanefreight.htb.
internal.inlanefreight.htb.
mail.inlanefreight.htb.

After trying, it seems like internal* is the only one responding
<img width="1204" height="652" alt="image" src="https://github.com/user-attachments/assets/c8a05157-d9bf-408d-9027-422e5337dce5" />

## 3rd Task
<img width="1668" height="452" alt="image" src="https://github.com/user-attachments/assets/2afc22ea-710f-45fc-b224-0a7edbbd56a5" />

Answer for this question can be found in the previous task's output. 

## 4th Task
<img width="1662" height="538" alt="image" src="https://github.com/user-attachments/assets/b729a28a-3cb1-48c8-bf58-20bae9ff38c4" />

This task is a bit tricky, first i was assuming that since we got the response from internal.inlanefreight, i should keep searching for the ip address inside it, but since i couldnt find it i took one step back and tried to enumerate using the same tool for the other subdomains. Since i kept getting no results, i tried DNSenum tool that was suggested in Academy, and got the flag from dev.inlanefreight.htb.
But after taking a look i still couldnt find the ip address so i tried different wordlists, and eventually after using the fierce-hostlist.txt i found the ip

<img width="2048" height="1014" alt="image" src="https://github.com/user-attachments/assets/f6ca7b4c-17df-46a1-918a-fe09acf77066" />

```dnsenum --dnsserver 10.129.79.180 --enum -p 0 -s 0 -o subdomains.txt -f /usr/share/seclists/Discovery/DNS/fierce-hostlist.txt dev.inlanefreight.htb```

that is the end of DNS 
