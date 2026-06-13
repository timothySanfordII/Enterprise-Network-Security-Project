# Nmap Scan Detection Lab
In this lab, I ...
  - Enable the IDS for the OPNsense firewall
  - Write an alert firewall rule on the Kali Linux VM
  - Upload that rule to the OPNsense firewall via Filezilla
  - Run an Nmap scan from the Kali Linux VM
  - Log the alerts of the Nmap scan in the OPNsense IDS

Step 1
---
Disabled the hardware checksum offload, hardware TCP segmentation offload, hardware large receive offload
This is recommended by OPNsense

<img width="1915" height="1079" alt="disable settings for IPS to work" src="https://github.com/user-attachments/assets/cbf7734a-8bfa-4d48-bbac-e12ba29df16d" />

Step 2
---
Set up the IDS for OPNsense
Enable the IDS, set the Interface to LAN, set the pattern matcher to Hyperscan, set Home network to the network hosting the Kali machine and OPNsense firewall, enabled syslog alerts

<img width="1913" height="1077" alt="IDS setup" src="https://github.com/user-attachments/assets/f6bb7237-5e6e-4512-a46a-d595c7182536" />

Step 3
---
