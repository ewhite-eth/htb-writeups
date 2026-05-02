# NFS

## 1st Task
<img width="1674" height="478" alt="image" src="https://github.com/user-attachments/assets/3eea7fd1-954e-445c-bf9e-c4d1442b902d" />

for this task we can first use nmap's NSE script "nfs*" which will enumerate the shares, list the content aswell as the status of them. 
<img width="1374" height="1442" alt="image" src="https://github.com/user-attachments/assets/bdb3a9cf-fe69-4f5c-b108-1ae4c51a05a6" />
this would be very useful if we were not given any share's and file's name beforehand, and we'd like to find out without mounting it to our system, we could also discover the available shares via showmount command. 
<img width="584" height="142" alt="image" src="https://github.com/user-attachments/assets/7d6c7d39-db7e-4370-9cb7-691dfd4a6d67" />

**Mounting** 
Now that we have found out about shares and contents, lets us now inspect them. For that we would need to create a dedicated directory, mount the shares and then proceed to investigation. 
<img width="1024" height="652" alt="image" src="https://github.com/user-attachments/assets/e9d22c2c-6d6d-4de2-a63e-c6ca303169b8" />

Heres the result we get after mounting the filesystem to our local directory.
