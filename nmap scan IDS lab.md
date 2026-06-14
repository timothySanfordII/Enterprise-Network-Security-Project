# Nmap Scan Detection Lab
In this lab, I ...
  - Enabled the IDS for the OPNsense firewall
  - Wrote an alert firewall rule on the Kali Linux VM
  - Uploaded that rule to the OPNsense firewall via Filezilla
  - Ran an Nmap scan from the Kali Linux VM
  - Logged the alerts of the Nmap scan in the OPNsense IDS

Step 1
---
Disabled the hardware checksum offload, hardware TCP segmentation offload, hardware large receive offload
This is recommended by OPNsense

<img width="1915" height="1079" alt="disable settings for IPS to work" src="https://github.com/user-attachments/assets/cbf7734a-8bfa-4d48-bbac-e12ba29df16d" />

Step 2
---
Set up the IDS for OPNsense
Enabled the IDS, set the Interface to LAN, set the pattern matcher to Hyperscan, set Home network to the network hosting the Kali machine and OPNsense firewall, enabled syslog alerts

<img width="1913" height="1077" alt="IDS setup" src="https://github.com/user-attachments/assets/f6bb7237-5e6e-4512-a46a-d595c7182536" />

Step 3
---
Created a rule file to aleart of any Nmap scan on the OPNsense firewall's IP

<img width="765" height="627" alt="The working customnmap rules " src="https://github.com/user-attachments/assets/b02bbef5-855e-45c9-b2e9-ffbd8bf6c1e7" />


Step 4
---
Enabled Secure Shell Access to OPNsense

<img width="1902" height="1076" alt="ENable Secure Shell access" src="https://github.com/user-attachments/assets/60dc6942-c72b-4802-ba1b-d46c7efb018f" />

Step 5
---
Installed Filezilla on Kali Linux

<img width="708" height="582" alt="install filezilla on Kali" src="https://github.com/user-attachments/assets/26fb960f-997d-4545-8a92-51d500433b0e" />

Step 6
---
Connected to OPNsense Firewall on Filezilla

<img width="1913" height="1063" alt="Filezilla connecting to opnsense" src="https://github.com/user-attachments/assets/a61150ce-cc28-47af-9e17-8be58cfdd8c0" />

Step 7
---
Created .xml file to reference the nmap rule file created

<img width="1261" height="763" alt="customnmap xml file" src="https://github.com/user-attachments/assets/a671c459-dd8b-4f0e-b900-b4b803240371" />

Step 8
---
Transferred .xml file from Kali to OPNsense via Filezilla

<img width="1907" height="1077" alt="customnmap xml to opnsense" src="https://github.com/user-attachments/assets/2ed53f34-7826-4d7a-bec3-78a2b5adc5b1" />

Step 9
---
Started a python http server to serve the rule file to OPNsense when the .xml file queries for it

<img width="1906" height="1075" alt="python http server" src="https://github.com/user-attachments/assets/01bea10c-19ee-441c-8fef-28589bc4f61b" />

Step 10
---
Reloaded Download Tab in Intrusion Detection Services on OPNsense GUI, populated customnmap rules, downloaded and enabled the rule

<img width="1911" height="1074" alt="download and enable customnmap rules in opnsense gui" src="https://github.com/user-attachments/assets/1e6eabe7-fabc-4488-93df-2c83aad7efcc" />

<img width="1914" height="1079" alt="customnmap rule added to IDS" src="https://github.com/user-attachments/assets/fd4d220f-9167-4b6c-b9b1-32869dc2db1f" />

Step 11
---
Ran Nmap scan on OPNsense VM

<img width="830" height="637" alt="nmap scan to test custom rule" src="https://github.com/user-attachments/assets/a1f7e636-98c6-4665-becf-6afeaf973dcd" />

Step 12
---
Logged alerts of Nmap scan being ran 

<img width="1917" height="1069" alt="Alert log of nmap scan following nmap rule" src="https://github.com/user-attachments/assets/1c5727d0-fc1e-45c2-b361-a185a9af56e6" />

---
# See "Lessions Learned.md" for troubleshooting needed during lab
















