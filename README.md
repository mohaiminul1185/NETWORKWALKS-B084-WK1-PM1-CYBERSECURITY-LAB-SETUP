# NETWORKWALKS-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP

# Cybersecurity Lab Environment Setup

building an isolated virtual lab for penetration testing and ethical hacking practice

##  Project Overview

This project outlines the deployment of an isolated virtual cybersecurity laboratory using Oracle VM VirtualBox and Kali Linux. The goal is to establish a secure sandbox for practicing network reconnaissance, scanning, and traffic evaluation without impacting the host environment.

---

## Objectives & Lab Purpose

- Deploying VirtualBox and setting up a private NAT Network (10.0.0.0/24)
- Installing and configuring Kali Linux with static IP mapping (10.0.0.2/24)
- Taking VM snapshots for safe rollback checkpoints.
- Documenting configurations, troubleshooting steps, and test validations.


## Lab Configuration & Architecture

  Component       |  Configuration                          
 -----------------| ---------------------------------------- 
  Host OS         | Windows 10 (8 GB RAM)                    
  Hypervisor      | Oracle VM VirtualBox 7.2                 
  Security OS     | Kali Linux 2026.3 (2 GB RAM)             
  Virtual Network | NAT Network (10.0.0.0/24)              
  Kali IP Address | 10.0.0.2/24 (Gateway: 10.0.0.1)      



# Lab Setup Procedure (Summary)

**Install 7-Zip & VirtualBox:** Set up extraction utilities and the hypervisor layer.
 **Create NAT Network:** Configured NatNetwork with IPv4 prefix 10.0.0.0/24









 
<img width="572" height="975" alt="image" src="https://github.com/user-attachments/assets/6650e439-b517-49dc-bd90-767c8a97c6c8" />











**Import Kali Linux:** Allocated virtual hardware specs and attached the NAT Network adapter.















<img width="1711" height="974" alt="image" src="https://github.com/user-attachments/assets/4e8cf3e6-0760-4b73-9a4e-cbb4b2e3d584" />















**Configure Static IP:** Assigned static IPv4 10.0.0.2 and DNS 8.8.8.8 to Kali Linux.
















<img width="787" height="528" alt="image" src="https://github.com/user-attachments/assets/1a8c26e5-48e3-4133-9cc9-2b5142a0604c" />

 













   
 **Create Snapshot:** Locked a clean baseline state named lab setup















 <img width="1007" height="776" alt="image" src="https://github.com/user-attachments/assets/a5564753-c796-441e-b88d-cd6a8a200813" />













# 🔎 Lab Verification

After completing the network captures and security analyses, I verified the integrity of my investigation results inside the toolkit by isolating traffic patterns, reassembling unencrypted data streams, and mapping indicators of compromise.

| ✅ Security Test & Verification | 🧾 Applied Wireshark Filter / Path | 🎯 Practical Results & Discoveries |
| ----------------------------- | ---------------------------------- | ---------------------------------- |
| 🐉 Attacker Identification     | `tcp.flags.syn == 1`               | Detected high-frequency Reconnaissance from `192.168.10.66` |
| 📡 Closed Port Analysis       | `tcp.flags.reset == 1`             | Isolated `[RST, ACK]` flags to verify closed server ports |
| 🌍 Network Volume Audit       | `Statistics > Conversations`       | Bidirectional frame mapping verified total of 44 network probes |
| 🔐 Credential Leak Inspection | `tcp.stream eq 5`                  | Extracted plain-text chat login credentials: `Tiger#4821` |
| 🔎 Directory Manipulation Check| `http.request.uri contains "download"`| Tracked unauthorized retrieval of internal file `report.txt` |
| 🧰 VoIP Artifact Recovery     | `Telephony > VoIP Calls`           | Replayed RTP stream via G.711 codec to extract voice evidence |



# 🐞 Problems Encountered & Solutions

Documenting real-world infrastructure roadblocks and applied technical remediations.

## Problem 1. Microsoft Defender Windows Flagging Kali Linux Archive as a Threat
While downloading the pre-configured Kali Linux virtual machine package on the Windows 10 host system, Microsoft Defender Antivirus immediately flagged the archive file as a severe security threat and blocked the download pipeline.
- **The Core Cause:** Kali Linux natively contains hundreds of integrated advanced tools used for penetration testing and vulnerability assessments, which Windows signatures automatically trigger as potentially dangerous programs (False Positive).
- **The Solution:** I temporarily deactivated the Real-time Protection shield inside Microsoft Defender to bypass the blockade and successfully complete the extraction process. Once the deployment container was mapped, the antivirus framework was immediately re-enabled to maintain the host OS security integrity.

---

## Problem 2. Kali Linux Virtual Machine Network Protocol Initialization Failure
Upon importing the Kali framework, the interface configuration wizard failed to dynamically request network resources, throwing connectivity errors inside the guest terminal layout.
- **The Core Cause:** The interface adapter configuration within the system initialization parameters was defaults-mapped to enforce strict dynamic tracking via **DHCP**. However, the static configurations of our managed cybersecurity lab network parameters clashed with the dynamic lease allocation architecture.
- **The Solution:** I manually disabled the DHCP dynamic allocation checkbox within the network configuration interface, disabling dynamic configurations completely. I then executed a clean hardcoded manual assignment to map the static parameters perfectly, instantly resolving the connectivity roadblock.


# 💡 What I Learned

- Differentiating standard NAT from managed NAT Networks for inter-VM communication.
- Managing hypervisor adapter settings and static Linux network configurations.
- Maintaining system integrity via VirtualBox snapshots and standard technical documentation.

---



🔗 Tools & Resources
7-Zip: https://7-zip.org/download.html 

VirtualBox: https://virtualbox.org/wiki/Downloads 

Kali Linux: https://kali.org/get-kali 





# 👤 Author & Project Info

Md Mohaiminul Islam 

Cybersecurity Intern Batch B084


LinkedIn:   



github: https://github.com/mohaiminul1185/NETWORKWALKS-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP/edit/main/README.md


Program: Networkwalks Cybersecurity Internship | Week 01
