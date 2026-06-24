# High Availability Lab
### In this lab, I ...
  - Cloned the OPNSense Firewall, creating Master Firewall vm and Backup Firewall vm
  - Configured both Firewall vms with different LAN IP addresses in 10.200.200.0 network
  - Opened third network adapter on both firewall machines to function as link between both firewall named "pfSync"
  - Assigned both pfSync network adapters with different IP addresses in 10.0.0.0 network
  - Created shared virtual LAN IP address and shared virtual WAN IP address on both firewall vms which represents the OPNSense Firewall prior to lab (10.200.200.254/24 LAN | 10.0.2.254/24 WAN)
  - Ensured Master Firewall had lower "skew" (0) then Backup (100), ensuring Master runs over Backup when both are on
  - Created Firewall rules for pfsync interfaces for both Master and Backup
  - Enabled and configure High Availability on Master and Backup
  - Created Hybrid NAT outbound traffic firewall rules for both Master and Backup

### Tested by:
  - Pinged Virtual LAN IP, LAN IP of Master Firewall, and LAN IP of Backup Firewall
  - Simulated disconnecting Master Firewall
  - While Master Firewall stopped receiving/returning pings, Virtual LAN IP and Backup Firewall continued to ping
  - Master Firewall could go down and Backup Firewall can be transitioned to seamlessly. End user's workflows would not be disrupted by transition

Step 1
---
In VirtualBox, clone OPNSense Firewall to create Master and Backup VMs
<img width="1919" height="1071" alt="clone master" src="https://github.com/user-attachments/assets/8423066a-d14b-45f6-a378-0c20fdcd5038" />
<img width="1915" height="1079" alt="master and backup" src="https://github.com/user-attachments/assets/314dbca0-cbbb-406e-a1ce-ce458dda8d88" />

Step 2
---
Confirmed NatNetwork of 10.0.2.0/24 is being used by VirtualBox
<img width="1917" height="1079" alt="nat network" src="https://github.com/user-attachments/assets/67e150c9-4b21-4231-83cb-93f9fd084e4f" />

Step 3
---
  - Changed Network Adapter 1 to NatNetwork, Adapter 2 to internal network, Adapter 3 to pfsync
  - Left Promiscuous Mode to "Allow" on WAN and LAN adapters but "Deny" on pfsync linking adapter
  - Repeated the same for the Backup Firewall VM
<img width="1910" height="1079" alt="added firewall master to NatNetwork in adapter 1" src="https://github.com/user-attachments/assets/e0052f7d-8c1a-4c1d-902e-5744e563c87b" />
<img width="1909" height="1077" alt="Master adapter 2 for LAN" src="https://github.com/user-attachments/assets/668becbf-b75e-4888-b663-280fa22e63c8" />
<img width="1919" height="1079" alt="Adpater 3 for pfsync" src="https://github.com/user-attachments/assets/b12b07e7-eee9-4eb0-b0d5-736d98a15338" />

Step 4
---
  - Started Backup Firewall VM
  - In terminal, changed LAN interface IP to 10.200.200.252
<img width="1917" height="1079" alt="set interface for LAN to 10-200-200-252 p3" src="https://github.com/user-attachments/assets/38dd09b4-72b4-4f68-954b-46e62a3a404f" />

Step 5
---
  - Started Kali Linux VM and Master Firewall VM
  - Connected Kali VM to Master Firewall VM GUI and changed LAN interface to 10.200.200.251
<img width="1917" height="1079" alt="change master uo ti 10-200-200-251" src="https://github.com/user-attachments/assets/85730f12-69f2-42fd-b6f3-c50b4dc42254" />

Step 6
---
  - Opened another web tab to connect Kali VM to Backup Firewall VM
  - Set em2 interface to pfsync on both Master Firewall VM GUI and Backup Firewall VM GUI
<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/2cd59ebc-6930-4135-ac02-e56d8eae834f" />
<img width="1919" height="1079" alt="pfsync assignment to interface em2 on backup p2" src="https://github.com/user-attachments/assets/2a8d662c-c1ad-4eae-b1ab-8564f79c5eed" />

Step 7
---
Enabled pfsync interfaces and assigned static 10.0.0.1/24 IP for Master Firewall VM and 10.0.0.2/24 IP for Backup Firewall VM
<img width="1913" height="1079" alt="enable pfsync interface on master p1" src="https://github.com/user-attachments/assets/5cb48506-5e7c-4127-b6cf-715c852f6675" />
<img width="1919" height="1079" alt="enable pfsync interface on master p2" src="https://github.com/user-attachments/assets/09652c46-4372-47a6-9108-cfa505f7bd85" />
<img width="1919" height="1073" alt="enable pfsync interface on backup" src="https://github.com/user-attachments/assets/f5d524db-1a52-4766-8572-c4782b1c0fa4" />

Step 8
---
For both firewall VMs, created firewall rules to allow traffic on pfSync interface
<img width="1917" height="1077" alt="create firewall for pfsync interface on backup" src="https://github.com/user-attachments/assets/0b0ce1f3-fd1b-46ce-a6d0-cef5c19d27ab" />
<img width="1919" height="1079" alt="create firewall for pfsync interface on backup p2" src="https://github.com/user-attachments/assets/3f1722e1-09ba-487f-9067-520138bbbbe8" />
<img width="1919" height="1079" alt="create firewall for pfsync interface on master" src="https://github.com/user-attachments/assets/4c7b4fa6-3223-4f53-ae8e-a084793f1df7" />

Step 9
---
  - Using CARP mode, created virtual LAN IP of 10.200.200.254/24 and virtual WAN IP of 10.0.2.254/24 on both Master Firewall and Backup Firewall
  - Configured "Adskew" was 0 for LAN & WAN virtual IPs on Master Firewall and 100 for LAN & WAN virtual IPs on Backup Firewall. This ensures Master Firewall is used if both firewalls are running
<img width="1919" height="1079" alt="create shared LAN virtual IP on master" src="https://github.com/user-attachments/assets/de02a2b0-a6f3-483b-a503-0c24390828fe" />
<img width="1919" height="1079" alt="create shared WAN virtual IP on master" src="https://github.com/user-attachments/assets/9feecb92-f113-4cbe-b3a3-609c4e501dcd" />
<img width="1919" height="1079" alt="complete virtual LAN and WAN for master" src="https://github.com/user-attachments/assets/2561e20f-cf19-4cdf-906d-63a42cb425d7" />
<img width="1915" height="1079" alt="create shared LAN virtual IP on backup" src="https://github.com/user-attachments/assets/9de9ec77-11c1-424c-b1ef-5aefcccf6392" />
<img width="1919" height="1079" alt="create shared WAN virtual IP on backup" src="https://github.com/user-attachments/assets/5e5907f3-647f-42e4-b49d-5e8527654023" />
<img width="1919" height="1079" alt="complete virtual LAN and WAN for backup" src="https://github.com/user-attachments/assets/6109184e-936c-42dc-a9bb-cfd6d754d10c" />

Step 10
---
  - Set High Availability Settings for both Master Firewall and Backup Firewall, each one uses the other's pfsync IP address as the "Synchronize Peer IP"
  - Only had to configure "Synchronization Settings" for Master as Backup would not log into another VM if it went down
<img width="1919" height="1079" alt="set High Availability settings in main p1" src="https://github.com/user-attachments/assets/c9c4e849-5fd7-4b7d-a3bb-39c70252341b" />
<img width="1919" height="1079" alt="set High Availability settings in backup" src="https://github.com/user-attachments/assets/579cfc62-a54d-4b5e-a996-9f1d1f6db6cc" />

Step 11
---
Create Hybrid Outbound NAT firewall rule to NAT traffic to to 10.0.2.254. Did this on both Master and Backup Firewalls
<img width="1906" height="1079" alt="nat outbound traffic to VIP WAN on master p1" src="https://github.com/user-attachments/assets/f85f84a6-1bfd-414d-9c32-c8e3204c22d0" />
<img width="1919" height="1075" alt="nat outbound traffic to VIP WAN on master p2" src="https://github.com/user-attachments/assets/3eb6cebf-386d-4f12-9341-2e4aa3c76bf4" />
<img width="1919" height="1079" alt="confirm hybrid outbound nat is checked and WAN rule is applied on master" src="https://github.com/user-attachments/assets/b76301f0-bb6f-46e6-b2c6-79d6c6dfb7e2" />
<img width="1918" height="1079" alt="create same firewall rule confirm hybrid outbound nat is checked and WAN rule is applied on backup" src="https://github.com/user-attachments/assets/a95787eb-7429-42c7-b316-9b6b26916ff1" />

Step 12
---
### Tested by...

- Pinged Virtual LAN IP (10.200.200.254), Master Firewall LAN IP (10.200.200.251), and Backup Firewall LAN IP (10.200.200.252)
- Disconnected WAN and LAN adapters for Master Firewall
- Observed how Master LAN becomes "unreachable" but because the Backup Firewall can still be pinged, the Virtual LAN IP can still be pinged
<img width="1919" height="1079" alt="able to ping virual IP, IP of master, IP of backup" src="https://github.com/user-attachments/assets/41b8579b-5266-45a2-b59a-ce19d0a208cb" />
<img width="1919" height="1079" alt="disconnected cable connected for adapter 1 and 2 for Master firewall, simulate it going down" src="https://github.com/user-attachments/assets/cfcd26b3-46ec-4555-93f8-806ef264f069" />
<img width="1917" height="1079" alt="shows 10-200-200-254 stayed reachable as backup stayed on and master became unreachable" src="https://github.com/user-attachments/assets/8ed2f227-d8c9-4da1-9a7a-cec06a115efc" />

---
# Did not need to troubleshoot any errors for this lab, nothing to add to Lessons Learned.md







