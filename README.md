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
this project documents hands-on practical commands for;
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
paro=_
paro.summary()
sniff(iface="br-internal")
ctrl c
paro2=_
paro2.summary()
sniff(iface="br-internal", filter = "icmp", count = 3
... : )
ctrl c
paro3=_
paro3.summary()
it filters for icmp only
paro3.nsummary()
paro3[3] type=echo-reply
paro3[2] type=echo-request
