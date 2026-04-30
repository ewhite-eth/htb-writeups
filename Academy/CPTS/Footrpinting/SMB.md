# SMB
Overall, all the tasks are related to enumerating SMB
**Task 1**

<img width="1698" height="466" alt="image" src="https://github.com/user-attachments/assets/5e894264-82e8-49c1-8529-5e56ff19e54a" />

here, we can just perform basic banner grabbing using nmap's script --script=banner
<img width="1250" height="332" alt="image" src="https://github.com/user-attachments/assets/d730d795-ffe0-4386-b55d-5fafa5ba6806" />

**Task 2**

<img width="1680" height="472" alt="image" src="https://github.com/user-attachments/assets/9cbb17a9-fc24-4683-b0d3-4e19d30b1c38" />

To solve this task, we need to enumerate the server, there are several ways for that, whatever we choose, we need to establish connection with SMB. 
1. Connecting to the SMB anonymously and listing shares 
<img width="1808" height="340" alt="image" src="https://github.com/user-attachments/assets/88a6f9b4-ee10-4860-9c42-9bf4caa67967" />
```
smbclient -N -L //10.129.73.123
```

2. Using NSE (nmap script engine)
   <img width="1320" height="536" alt="image" src="https://github.com/user-attachments/assets/8635a4cf-68db-4602-bdff-7af963b9add8" />

```
sudo nmap -sC -p139,445 10.129.73.123
```

3. SMBmap
<img width="1828" height="636" alt="image" src="https://github.com/user-attachments/assets/aa5f61a8-d104-4b5c-b1f2-5503ce35ee47" />

``` 
smbmap -H 10.129.73.123 
```

4. CrackMapExec
   <img width="1868" height="290" alt="image" src="https://github.com/user-attachments/assets/b6c1a47e-2b5b-414b-b544-1626afe1cd04" />
```
crackmapexec smb 10.129.73.123 --shares -u "" -p ""
```

however, as we can see, the Nmap couldnt list out the shares while other tools did, thats why its important to use several tools and not rely on only one. 

**Task 3**

<img width="1682" height="476" alt="image" src="https://github.com/user-attachments/assets/43f221d5-3112-4966-ba72-68ffa82f0ec7" />

For this task, we have to connect to the server and then either use cat inside the smb server, or download the file using get method and then open in on our side. 
<img width="1098" height="566" alt="image" src="https://github.com/user-attachments/assets/4590def1-bbed-4f6b-b4f7-46202ecc281e" /> (btw, use get cuz cat outputs wrong flag for some reason)

its worth mentioning the part where i used !<> when running cat command. The reason is that it allows running the command locally on our shell and not interrup to tthe connection with the SMB server, so that we dont reopen it. 


**Task 4**
<img width="1692" height="606" alt="image" src="https://github.com/user-attachments/assets/c183cb83-a522-4423-80e7-838675169bb4" />
To find out information about domain, we could use rcpclient as our tool, as it performs MS-RCP functions

<img width="842" height="396" alt="image" src="https://github.com/user-attachments/assets/98644dd4-e2d2-46c2-a971-4b56b57cab17" />
```
rpcclient -U "" 10.129.73.123
```
**Task 5**
<img width="1674" height="506" alt="image" src="https://github.com/user-attachments/assets/3e061afc-1076-4c1c-92c4-611c60f834fb" />
Once we got rpcclient and the name of the share, we use the command of rpcclient netsharegetinfo and the name of the specific share that we want to enumerate

<img width="1678" height="504" alt="image" src="https://github.com/user-attachments/assets/a0c7d33d-aa58-4f60-9fac-2dcdf88ceebb" />
```
rpcclient $> netsharegetinfo sambashare
```
<img width="1672" height="522" alt="image" src="https://github.com/user-attachments/assets/d21be01b-bf70-451c-9cc9-741de6ba32ad" />




