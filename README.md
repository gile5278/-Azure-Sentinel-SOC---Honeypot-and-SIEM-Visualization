# 🛡️ Active Directory Attack Lab

A hands-on security lab simulating common Active Directory (AD) attacks and post-exploitation techniques.  
This project is built to learn and demonstrate offensive security concepts, privilege escalation, and detection.

---

## ✅ Project Overview

- 🖥️ Simulated Windows Active Directory environment
- 🎯 Executed common attacks like Kerberoasting, Pass-the-Hash, ACL abuse
- 🔍 Detected malicious activities using Windows Event Logs and Splunk
- 🧠 Documented attack flow, tools used, and defense strategies

---

## ⚙️ Lab Setup

| Component | Details |
|----------|---------|
| Domain Controller | Windows Server 2019 (Active Directory + DNS) |
| Victim Machine | Windows 10 |
| Attacker Machine | Kali Linux |
| Tools Used | Mimikatz, BloodHound, SharpHound, Rubeus, Impacket, PowerView, Splunk |

🛠️ _You can find detailed setup instructions in `/docs/setup.md` (Coming soon)_

---

## 🧪 Attacks Performed

| Attack Technique | Tool Used | Goal |
|------------------|------------|------|
| Kerberoasting | Rubeus | Crack service account password |
| Pass-the-Hash | Impacket | Lateral movement |
| Enumeration | PowerView, BloodHound | Map domain trust and access |
| ACL Abuse | BloodHound | Privilege escalation to Domain Admin |

---

## 📸 Screenshots

> _Coming soon: Add screenshots of BloodHound graph, terminal commands, Splunk dashboard here_

---

## 🔍 Detection & Logging

- Monitored Event IDs: `4769`, `4624`, `4688`
- Sample Splunk Search Queries (Coming soon)

---

## 📚 Key Learnings

- How AD environments can be abused by attackers
- Importance of visibility and monitoring (logs/SIEM)
- How attackers move laterally and escalate privileges

---

## 📎 References

- [BloodHound](https://github.com/BloodHoundAD/BloodHound)
- [Impacket](https://github.com/SecureAuthCorp/impacket)
- [TryHackMe: Attacktive Directory](https://tryhackme.com/room/attacktivedirectory)

# Active Directory Attack Lab (Based on Josh Madakor's YouTube Guide)

This is a hands-on Active Directory lab setup and attack simulation, built and tested by following Josh Madakor's video guide:  
👉 [How to Build an Active Directory Lab for Free (2025)](https://www.youtube.com/watch?v=g5JL2RIbThM)

## 🔧 Lab Components

- **Windows Server 2019** (Domain Controller)
- **Windows 10** (Domain-joined client)
- **Kali Linux** (Attacker machine)

## 🎯 Purpose

This project demonstrates:

- Setting up an AD domain environment in VirtualBox
- Performing attacks such as:
  - Enumerating users
  - Kerberoasting
  - Pass-the-Hash
  - Privilege escalation

## 📄 Setup Instructions

The full setup guide can be found here:  
📘 [docs/setup.md](./docs/setup.md)

## 📸 Screenshots

*(Add some screenshots here later of successful attacks, bloodhound graph, etc)*

## 🔒 Disclaimer

This lab is intended for educational purposes only.

