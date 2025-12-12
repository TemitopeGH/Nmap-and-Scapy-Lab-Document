# Nmap-and-Scapy-Lab-Document
This repository documents hands-on exercises with Nmap and Scapy, covering network scanning, packet analysis, and security assessment techniques

## Table of Contents <br>
### Overview <br>
### Tools Used <br>
### Environment Setup <br>
### Nmap Commands <br>
### Wireshark & tcpdump <br>
### Scapy Usage <br>
### Screenshots <br>
### Conclusion <br>

## Overview
This project documents hands-on practical commands for;
- Host discovery
- Port enumeration
- SMB enumeration
- Packet capture
- Packet filtering
- Protocol analysis

## Tools Used
- Nmap - Network scanning and enumeration
- Wireshark - Packet analysis
- tcpdump - Command-line packet sniffer
- Scapy - Packet manipulation and network automation
- Kali Linux - (VMware/VirtualBox)

## Environment Setup
### Component........... Details
 OS......................Kali Linux <br>
 Interface...............eth0,br-internal <br>
 Target IP...............10.6.6.23 <br>
 Network Range...........10.6.6.0/24 <br>

## Nmap Commands
- nmap -V
 to know the version of the Nmap

- nmap -sn 10.6.6.0/24
Hosts Discovery (Ping Sweep)

- sudo nmap -O 10.6.6.23
Operating system Detection and Open Ports

- nmap -p21 -sV -A -T24 10.6.6.23
Aggressive Service Detection, ftp server version, files on the host and permissions

- nmap -p139,445 -sV -A -T24 10.6.6.23
SMB Enumeration (Ports 139 & 445)

- nmap --script smb-enum-shares.nse -p445 10.6.6.23
numerate SMB Shares. Helps to see the weaknesses of the smb, hidden shares ($), security risk (Anonymous access)

- smbclient //10.6.6.23/print$ -N
Access SMB Shares. The command is used to connect to a Windows SMB share from a Linux/Kali/Unix terminal to login annonymously to any of the directories and exlore.
- list files:
ls

## Wireshark $ tcpdump
- pwd
View work directory

- ifconfig
Network interface and IP Address

- ip route
View Routing Table

- cat /etc/resolv.conf
Check DNS server

- tcpdump
captures traffic on the terminal

- sudo tcpdump -i eth0 -s 0 -w ladies.pcap
Capture packets recieved by filter after listening on eth0 and save to ladies.pcap

* ls to view if the files is saved

* open wireshark: <br>
click on file, open, kali, ladies.pcap and open

## Scapy Usage
- sudo su, enter password
To switch to privilege user

- man scapy
Manual page for the tool

- sudo su <BR>
  scapy <br>
Launch Scapy

- help()
  Get Help
  
- ls()
List all the available protocols

- sniff()
sniff helps to capture network traffic similar to wireshark <br>
stop with ctrl + C

- ping google.com on another terminal, ctrl c to stop it.
- ping -c 4 google.com to ping just 4 packets

- ctrl c to stop the sniff, <Sniffed: TCP:2332 UDP:537 ICMP:82 Other:33>
paro=_ <br>
paro.summary() <br>
sniff(iface="br-internal") <br>
ctrl c <br>
paro2=_ <br>
paro2.summary() <br>
sniff(iface="br-internal", filter = "icmp", count = 3 <br>
... : ) <br>
ctrl c <br>
paro3=_ <br>
paro3.summary() <br>
it filters for icmp only <br>
paro3.nsummary() <br>
paro3[3] type=echo-reply <br>
paro3[2] type=echo-request <br>

## Screenshots
<img width="1366" height="702" alt="Screenshot_2025-12-12_17_37_50" src="https://github.com/user-attachments/assets/391b39a3-9d50-4013-8266-1966f8012396" />

<img width="1366" height="702" alt="Screenshot_2025-12-12_17_46_15 Host Discovery" src="https://github.com/user-attachments/assets/e815cb87-e744-44aa-8720-45e7a5ef8a20" />

<img width="1366" height="702" alt="Screenshot_2025-12-12_17_48_49 operating system detection and open ports" src="https://github.com/user-attachments/assets/1fb94e29-0909-4f99-ac11-ce2f28fd1da8" />

<img width="1366" height="702" alt="Screenshot_2025-12-12_18_17_55 Aggressive Service Detection" src="https://github.com/user-attachments/assets/378f429b-6f4c-434e-9d4e-c3a90d0bf9e9" />

<img width="1366" height="702" alt="Screenshot_2025-12-12_18_26_58 wireshark" src="https://github.com/user-attachments/assets/8de6f270-b0bd-43b8-97de-40aa02f654ad" />

<img width="1366" height="702" alt="Screenshot_2025-12-12_18_20_44 SMB Enumeration" src="https://github.com/user-attachments/assets/abefbf0a-176b-4992-bf36-b7824b138cd2" />

<img width="1366" height="702" alt="Screenshot_2025-12-12_18_24_00 scapy" src="https://github.com/user-attachments/assets/94f4ef20-f8ab-4198-b2d9-ac86edd987cc" />

## Conclusion
This README serves as a professional reference for:
- Network reconnaissance
- Enumeration
- Traffic capture
- Packet analysis
- Scapy automation

It is suitable for:
- Cybersecurity students
- SOC analysts
- Penetration testing beginners
- Home lab builders
  
