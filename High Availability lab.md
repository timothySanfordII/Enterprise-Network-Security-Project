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
