# Network Scanning and Risk Assessment

This project shows how to use **Nmap** for network reconnaissance and discusses the **security risks of open ports**. 
It includes practical scanning outputs and an analysis of vulnerabilities found in a local network.

Files Included

`networkscan.txt`: Basic Nmap TCP SYN scan (`-sS`) on the 192.168.0.123/24 subnet.  
`versioncan.txt`: Version detection scan (`-sV`) for identifying services and their versions.  
`risksofopenports.txt`: Summary of common risks linked to open ports and suggested ways to reduce them.

---

Tools Used

**Nmap 7.95** for network scanning and service version detection.  
**Linux Terminal** as the environment for running scans.

## Scan Results Summary

### Discovered Devices

| IP Address       | MAC Address            | Notable Open Ports         |
|------------------|------------------------|-----------------------------|
| 192.168.0.1      | TP-Link Limited        | 22 (SSH), 53 (DNS), 80 (HTTP), 1900 (UPnP) |
| 192.168.0.105    | Unknown                | No response (all filtered) |
| 192.168.0.110    | Unknown                | 5060 (SIP - filtered)      |
| 192.168.0.112    | Unknown                | All closed                 |
| 192.168.0.119    | Cloud Network Tech     | All filtered               |
| 192.168.0.123    | Unknown                | All closed                 |
| 192.168.0.122    | Unknown                | All closed                 |

### Service Versions on 192.168.0.1

| Port | Service | Version |
|------|---------|---------|
| 22   | SSH     | Dropbear sshd 2012.55 |
| 53   | DNS     | Generic DNS (FORMERR) |
| 80   | HTTP    | TP-LINK WAP config    |
| 1900 | UPnP    | Portable SDK 1.6.19   |

Risks of Open Ports

From `risksofopenports.txt`, key risks are:

1. Unauthorized Access - Example: weak SSH credentials.
2. Exploitation of Vulnerable Services – Outdated HTTP servers.
3. Port Scanning and Fingerprinting – Helps attackers plan exploits.
4. Misconfiguration Exposure – Internal services accessible publicly.
5. Malware Communication – Open ports can serve as command and control channels.
6. Data Leakage – Anonymous access to files and services.

Mitigation Tips:
- Close unused ports.
- Use firewalls and IP restrictions.
- Keep services updated and monitored.

---

## How to Use
1. open linux terminal
   use 'ifconfig' to find our ip adderss
2. search nmap tool in terminal #it is preinstalled in linux
   #this tool is used to scan the network of target ip adderss
3. Run a basic scan:  
   sudo nmap -sS 192.168.0.123/24  #The -sS option in Nmap stands for a TCP SYN scan, also known as a "half-open scan".
4. Detect service versions:  
   sudo nmap -sV 192.168.0.123/24
5. Analyze the results to identify risks and take actions.
