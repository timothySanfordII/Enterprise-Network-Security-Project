# Lessons Learned
Initial Configuration
---
   - Statically assigning IP address to virtual machine within Terminal
<img width="1895" height="1064" alt="command to change static IP" src="https://github.com/user-attachments/assets/2776723f-81e1-452f-a9cb-fe0138c96890" />
<img width="1904" height="1067" alt="kali linux network statically assign IP" src="https://github.com/user-attachments/assets/6be74ed2-59db-4949-93e3-3122ed3ac9f7" />

nmap scan IDS lab
---
### 1

   - Realized Kali VM was not properly configured to DNS when unable to download filezilla
   - Able to ping 8.8.8.8 but not google.com
   - Faced with a DNS issue
   - nano into /etc/resolv.conf file
        - added the following:
             - nameserver 8.8.8.8
             - nameserver 1.1.1.1
   - Now able to ping google.com and download Filezilla

<img width="725" height="591" alt="error downloading filezilla" src="https://github.com/user-attachments/assets/f3eb84aa-9113-4998-872c-b78b7c78906e" />

<img width="1909" height="1073" alt="DNS troubleshoot and Filezilla download" src="https://github.com/user-attachments/assets/c31ad512-f393-4448-864d-363adf458027" />

### 2

 - Accidently deleted /usr file for OPNsense VM while exploring Filezilla
 - Had to recreate OPNsense VM
 - Learned the importance of having working backups when making changes
 - Implemented use of snapshots in VirtualBox

<img width="857" height="600" alt="example of taking a vm snapshot" src="https://github.com/user-attachments/assets/2b271791-af08-4fc9-a70a-3c713171f17a" />
