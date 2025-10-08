
# 🛡️ Snort IDS/IPS Project  

## 📘 Overview  
This project demonstrates the setup, configuration, and testing of **Snort**, an open-source **Intrusion Detection and Prevention System (IDS/IPS)** used to monitor and protect network traffic from malicious activities.  
The objective is to simulate a realistic network security environment and showcase how Snort can detect and prevent attacks in real time.  

---

## 🎯 Objectives  
- Configure Snort in both **IDS** (Intrusion Detection System) and **IPS** (Intrusion Prevention System) modes.  
- Create and test **custom Snort rules** to detect malicious patterns.  
- Capture and analyze alerts generated from simulated attacks.  
- Integrate Snort with **Wireshark** and **Security Onion** for enhanced visibility and analysis.  

---

## 🧰 Tools & Technologies  
- **Snort** – Intrusion Detection & Prevention  
- **Wireshark** – Packet capture and network analysis  
- **Security Onion** – Security monitoring and log management  
- **Kali Linux** – Attack simulation and penetration testing  
- **VirtualBox** – Virtualized testing environment  

---

## ⚙️ Setup & Configuration  

1. **Install Snort** on Ubuntu or Security Onion VM.  
   ```bash
   sudo apt-get update
   sudo apt-get install snort -y
2. **Verify network interface** used for packet capture:
   ```bash
   ifconfig
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
