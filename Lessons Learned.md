# Lessons Learned
Initial Configuration
---
### 1
   - Statically assigned IP address to virtual machine within Terminal
<img width="1895" height="1064" alt="command to change static IP" src="https://github.com/user-attachments/assets/2776723f-81e1-452f-a9cb-fe0138c96890" />
<img width="1904" height="1067" alt="kali linux network statically assign IP" src="https://github.com/user-attachments/assets/6be74ed2-59db-4949-93e3-3122ed3ac9f7" />

### 2
   - Ran into issues installing Windows 11, I kept getting stuck in the shell when trying to upload the Windows 11 iso
   - After researching my issue, realized too much time was being spent on installing Windows machine and opted to use Windows 10 instead
   - Able to create Windows 10 machine without issue
   - Learned how to statically assign IP address to Windows machine
<img width="905" height="759" alt="change static IP p1" src="https://github.com/user-attachments/assets/1099cf52-596d-4334-b1dc-3f97ec7fbec7" />
<img width="940" height="772" alt="change static IP p2" src="https://github.com/user-attachments/assets/9fca119e-a46d-473d-b8f1-b8db45e3181f" />
<img width="989" height="856" alt="change static IP p3" src="https://github.com/user-attachments/assets/e66ca016-298d-47a6-a4bd-bce42463a204" />
<img width="847" height="722" alt="change static IP p4" src="https://github.com/user-attachments/assets/6e26b4c4-bb6e-43d1-ae6e-45f8a949450b" />

Nmap Scan IDS lab
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

Squid Web Proxy lab
---
### 1
Had to upgrade OPNSense from 26.1.6 to 26.1.10 in order to install Squid Web Proxy
<img width="1919" height="1079" alt="updated opnsense from 26-1-6 to 26-1-10" src="https://github.com/user-attachments/assets/4b98862e-cb0e-46c2-ad3e-7d6325109450" />
<img width="1896" height="1023" alt="updated opnsense from 26-1-6 to 26-1-10 p2" src="https://github.com/user-attachments/assets/e52b633b-b6f2-4d5e-a67d-14bcfff96e01" />

### 2

- Initially unable to receive any HTTPS traffic following creation of Transparancy Firewall rules
- Realized I had assigned port 3128 for both HTTP and HTTPS traffic
- Set 3128 for HTTP traffic and 3129 for HTTPS traffic, Squid Web Proxy then worked as intended
<img width="1919" height="1079" alt="Issue 1" src="https://github.com/user-attachments/assets/e0d0fa10-b39d-464d-b2c1-44f0eb618b0a" />
<img width="1919" height="1079" alt="Created firewall rule for transparancy proxy p4 for https" src="https://github.com/user-attachments/assets/85b4fd1b-33b2-41c7-88a9-c64cfeb29821" />
<img width="1915" height="1077" alt="changed portforwarding firewall to forward to 3129 to match squid proxy - resolved error" src="https://github.com/user-attachments/assets/5d1b6a24-d741-4b5e-aff5-6cca1b31f0cd" />

Zenarmor NGFW lab
---
   - Encountered error when trying to initiate Zenarmor ~ "Please disable interface Harware Offloadings"
   - Had to disable hardware checksum offload, hardware TCP segmentation offload, and hardware large receive offload
<img width="1919" height="1079" alt="zenarmor dashboard setup p4" src="https://github.com/user-attachments/assets/40a0a5ac-554e-49d5-82d9-b01f9753e640" />
<img width="1919" height="1079" alt="disabled top 3 in interfaces settings to resolve last error message" src="https://github.com/user-attachments/assets/d1c5b7d2-ddac-407a-a940-0b2a9fe6e017" />
<img width="1919" height="1079" alt="zenarmor dashboard setup p4-5" src="https://github.com/user-attachments/assets/81e07111-40e4-4a1c-8d83-ac8242d9ab01" />







