
# 🛡️ Snort IDS/IPS Project  

## 📘 Overview  
This project demonstrates the setup, configuration, and testing of **Snort**, an open-source **Intrusion Detection and Prevention System (IDS/IPS)** used to monitor and protect network traffic from malicious activities.  
The objective is to simulate a realistic network security environment and showcase how Snort can detect and prevent attacks in real time.  

---

## 🎯 Objectives  
- Configure Snort in both **IDS** (Intrusion Detection System) and **IPS** (Intrusion Prevention System) modes.  
- Create and test **custom Snort rules** to detect malicious patterns.
- Detect and log the following attacks:
- (a) ICMP Ping from Kali → Windows
- (b) SYN Scan (nmap -sS) from Kali → Windows
- (c) Block packets inline using Snort IPS (NFQUEUE) 

---
## 🌐 Network Topology
| Component                | IP Address                          | Role                 |
| ------------------------ | ----------------------------------- | -------------------- |
| 🧱 **pfSense (Gateway)** | `WAN 10.0.2.7/24` `LAN 10.0.3.1/27` | Router + Firewall    |
| 🐧 **Ubuntu Server**     | `10.0.3.10`                         | Snort IDS/IPS Sensor |
| 💀 **Kali Linux**        | `10.0.3.4`                          | Attacker Machine     |
| 🪟 **Windows Target**    | `10.0.3.11`                         | Victim Host          |

All VMs run on VirtualBox Internal Network (10.0.3.0/27) with promiscuous mode enabled on Ubuntu’s NIC.

---
## 📷 Topology Diagram:

   <img width="431" height="347" alt="image" src="https://github.com/user-attachments/assets/67a83464-0370-4dc0-89e2-6cba1bed8de9" />

---
## ⚙️ Environment & Configuration

- OS: Ubuntu {{version}} | Snort: v{{version}}
- HOME_NET: 10.0.3.0/27 in /etc/snort/snort.conf
- Rules: local.rules
  
Run Commands:
```bash

# IDS (alert mode)
sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3

# IPS (inline NFQUEUE mode)
sudo iptables -I FORWARD -j NFQUEUE --queue-num 0
sudo snort -Q --daq nfq --daq-var queue=0 -c /etc/snort/snort.conf -i enp0s3

```
## 🧾 Custom Rules (/etc/snort/rules/local.rules)

```bash
# 1000001 – ICMP Echo
alert icmp any any -> $HOME_NET any (msg:"ICMP Echo to HOME_NET"; sid:1000001; rev:1;)

# 1000002 – SYN Scan
alert tcp any any -> $HOME_NET 1:1024 (flags:S; msg:"SYN scan to HOME_NET"; sid:1000002; rev:1;)
```
💡 For IPS demo, change alert → drop in the rule and run Snort inline.

---
## 🧪 Test Procedure

1. Start Snort on Ubuntu:
```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3
```
2. From Kali:
```bash
# ICMP Ping
ping -c 4 10.0.3.11

# SYN Scan
nmap -sS -p1-1000 10.0.3.11
```
<img width="959" height="512" alt="SNORT IDS FOR ICMP" src="https://github.com/user-attachments/assets/4c8af512-bb39-4401-b915-ddedac5c1bc5" />
<img width="959" height="504" alt="SNORT IDS FOR TCP PORT SCAN" src="https://github.com/user-attachments/assets/639d3f1d-b8a8-4278-b3f6-f3af2ef7f2b0" />


---
## 📊 Results

1. Successfully detected and logged simulated intrusion attempts.
2. Verified Snort’s ability to operate in inline mode (IPS) to block malicious traffic.
3. Gained hands-on experience with rule writing, packet inspection, and threat response.
---
## 🧠 Key Learnings

1. Understanding the difference between IDS and IPS modes.
2. Writing and tuning Snort detection rules.
3. Analyzing packet captures for suspicious activity.
4. Strengthening knowledge of network security monitoring fundamentals.

---
## 📎 Future Improvements

1. Automate Snort alert reporting with Python scripts.
2. Integrate Snort logs into a SIEM dashboard using Splunk or ELK Stack.
3. Expand detection rules for DDoS, brute-force, and SQL injection attacks.
---
## 🔗 Connect with Me
<a href="https://linkedin.com/in/davidtheanalyst/" target="_blank"> <img src="https://img.shields.io/badge/-LinkedIn-0072b1?style=for-the-badge&logo=linkedin&logoColor=white" /> </a>
