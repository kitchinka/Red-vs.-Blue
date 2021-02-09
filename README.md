# Red-vs.-Blue
Penetration testing engagement of a vulnerable Apache web server using Kali Linux with monitoring from ELK Stack/Kibana. This project was performed on a remote desktop server. 

Second Project of Case Western Reserve University's Cybersecurity Boot Camp. 

## Network Topology
**Network Address Range**: 192.168.1.1-255

**Netmask**: 192.168.0/24

**Gateway**: 192.168.1.1

### Machines

Windows Host
  - OS: Windows
  - IPv4:  192.168.1.1
   
Kali
  - OS: Kali Linux
  - IPv4: 192.168.1.90
  
ELK
  - OS: Linux
  - IPv4: 192.168.1.100
  
Capstone
  - OS: Linux
  - IPv4: 192.168.1.105
  
## Red Team
Kali attacks Capstone. 

Vulnerabilities discovered:
  - Administrative Control
  - Brute Force
  - PHP Reverse Shell

Tools:
  - Nmap
  - Hydra
  - Crackstation.net
  - MSFconsole
  - MSFvenom
  - Meterpreter

## Blue Team 
ELK collects data from Capstone. 

Intrusions detected:
  - Port scan
  - Hidden directory request
  - Brute force attack
  - WebDAV connection
  
Queries used:
  - ICMP request message
  - Secret folder URL
  - Password Mismatch message
  - WebDAV URL path

## Hardening
Proposed alerts to set in ELK to detect future intrusions of the same nature. 
System hardening recommendations prevent future instrusions of the same nature. 

**Alarms**
  - \>5 ICMP packets
  - \>10 requests for /secret_folder
  - \>8 Password mismatch messages per IP address
  - \>10 network inbound packets to URL path /webdav
  - \>1 POST request to URL path /webdav
  
**System Hardening**
  - Configure firewall settings to filter ports
  - Remove references to /secret_folder from public-facing website
  - Strengthen password policy (15-20 characters, 1 each of alphanumeric ((upper- and lowercase)) and special characters, changed every 30 days, can't be same as last 3)
  - Add an IP whitelist to the firewall
      - If this is too strong, add a blacklist of known bad actors & create an account lockout policy
  - Take instructions for accessing the webDAV server offline
  - Move password hashes offline
  - Enable SSH key authentication
  - Disable PHP file uploads
  - Enable FTPS
  
