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
