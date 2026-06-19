# Squid Web Proxy Lab
In this lab, I ...
  - Created a self-signed trust certificate for the OPNSense firewall and installed it on the Windows 10 machine
  - Installed Squid Web Proxy as a pluggin to OPNSense
  - Created Firewall Transparency rules for HTTP and HTTPS traffic
  - Downloaded an open source, premade blacklist ACL from The Université Toulouse
  - Blacklisted the "Social media" category to block web access to social media sites
  - Created Firewall Bypass rules for HTTP and HTTPS traffic in the event "Social media" site access is attempted
  - Tested Web Proxy to ensure "Social media" sites could not be accessed but other sites can
  

Step 1
---
Created self-signed trust certificate 
<img width="1917" height="1079" alt="create web trust certificate" src="https://github.com/user-attachments/assets/8e39a8fa-af8c-43c5-b4d0-830751ab16a5" />
<img width="1919" height="1079" alt="create web trust certificate p2" src="https://github.com/user-attachments/assets/c8a5641e-ce21-4352-86aa-bbbf18ef5c57" />
<img width="1918" height="1079" alt="download cert" src="https://github.com/user-attachments/assets/c6ccad48-996a-4d98-b055-ee958d3baefa" />

Step 2
---
  - Downloaded certificate and converted file from .pem to .crt so Windows would recognize it
  - Installed certificate on Windows 10 machine and saved it to Trusted Root Certification Authorities folder
<img width="1918" height="1079" alt="download cert" src="https://github.com/user-attachments/assets/c65c39f5-4381-40a2-ba60-cf4ae91d8cf4" />
<img width="1919" height="1079" alt="renamed file from pem to crt" src="https://github.com/user-attachments/assets/3d552de9-929a-45db-9d28-6acee896cbae" />
<img width="1919" height="1079" alt="installed the cert" src="https://github.com/user-attachments/assets/c6517761-7eb0-4255-9116-ec731d9bc526" />
<img width="1919" height="1079" alt="saved to Trusted root " src="https://github.com/user-attachments/assets/f351a714-c2c0-416b-aafc-212b7db00886" />

Step 3
---
Installed Squid Pluggin to OPNSense
<img width="1917" height="1079" alt="added squid pluggin to opnsense" src="https://github.com/user-attachments/assets/12bc1bbb-48ed-4f7c-a546-2df508f6658f" />

Step 4
---
Enabled Squid Web proxy
<img width="1917" height="1079" alt="Enable Squid proxy" src="https://github.com/user-attachments/assets/5d16bc01-a898-42eb-8679-d8e5e65ec918" />

Step 5
---
Created firewall rules to redirect traffic through transparancy proxy for HTTP and HTTPS traffic
<img width="1919" height="1079" alt="Created firewall rule for transparancy proxy p1" src="https://github.com/user-attachments/assets/a6d1e591-44ac-498c-b0ae-e3347e4cf7de" />
<img width="1917" height="1079" alt="Created firewall rule for transparancy proxy p2" src="https://github.com/user-attachments/assets/e38d088b-08cc-4813-ad03-8d445fb0f363" />
<img width="1915" height="1077" alt="changed portforwarding firewall to forward to 3129 to match squid proxy - resolved error" src="https://github.com/user-attachments/assets/0e0650a1-d4d8-4ef1-8225-579dde65769c" />

Step 6
---
Set the Forward Proxy ports to match the previous firewall ports
<img width="1919" height="1079" alt="Configure squid web proxy- admin" src="https://github.com/user-attachments/assets/004e4794-14d1-46dd-980d-a518661f0edd" />

Step 7
---
Ensured nothing was set in the "Authentication Settings" for the "Forward Proxy". This would be used in a school or work environment for individuals to log in when accessing the web, it assist with logging website history on an individual basis
<img width="1915" height="1079" alt="confirm nothing is selected" src="https://github.com/user-attachments/assets/63d0756f-5e15-4782-906e-4257c2a030e0" />

Step 8
---
Created and downloaded blacklist pulling from open source, premade blacklist ACL from The Université Toulouse
<img width="1919" height="1079" alt="create blacklist " src="https://github.com/user-attachments/assets/5614bd62-338b-4f44-b3cb-12ebb0323e5b" />
<img width="1919" height="1079" alt="download acl" src="https://github.com/user-attachments/assets/95d6198b-f8a6-4404-9f1b-7ed8f1537e14" />

Step 9
---
Unselected all categories in the blacklist, selected Social networks, redownloaded blacklist, and applied blacklist
<img width="1919" height="1079" alt="categories populate for blacklist" src="https://github.com/user-attachments/assets/bccd682d-b88c-4033-a558-870ffa1d4e2e" />
<img width="1919" height="1079" alt="selected social_networks" src="https://github.com/user-attachments/assets/dcdb91b7-067d-4c62-a365-2c08482cad8d" />
<img width="1919" height="1079" alt="download acl 2nd time" src="https://github.com/user-attachments/assets/e0e160ca-863d-4228-8371-270a24dc61bd" />
<img width="1914" height="1079" alt="select apply to apply blacklist" src="https://github.com/user-attachments/assets/37c87048-bedd-45e1-b63b-c06bdc2ff9de" />

Step 10
---
Created Proxy Bypass firewall rules for HTTP and HTTPS traffic and repositioned them to come first amongst LAN firewall rules
<img width="1911" height="1079" alt="proxy bypass firewall rule p1" src="https://github.com/user-attachments/assets/de885048-3930-4311-a67e-5a4b3432ea26" />
<img width="1919" height="1075" alt="proxy bypass firewall rule p2" src="https://github.com/user-attachments/assets/16f277d7-07a1-4c51-a6c9-fae3f64837dc" />
<img width="1917" height="1078" alt="cloned bypass rule and did the same for https" src="https://github.com/user-attachments/assets/eeb22f64-b94f-4c85-87ee-d7f6779af90c" />
<img width="1919" height="1079" alt="repositioned rules to come before allowing rules and applied change" src="https://github.com/user-attachments/assets/657e73a7-cfc7-47f9-a29c-da436358fe98" />

Step 11
---
Restarted Squid Web Proxy service
<img width="1919" height="1079" alt="restarted web proxy service admin" src="https://github.com/user-attachments/assets/dc490669-7f55-4ab9-b171-b91ac2d6aa1d" />

Step 12
---
Confirmed able to access Youtube (non-social media site). Confirmed access to Facebook is blocked (social media site).
<img width="1919" height="1079" alt="able to access youtube" src="https://github.com/user-attachments/assets/8480e604-e252-4d93-a5fb-95f955706a4d" />
<img width="1919" height="1079" alt="not able to access Facebook - like intended" src="https://github.com/user-attachments/assets/4d5e0f06-66bd-4c32-ad81-13c81458f99b" />






