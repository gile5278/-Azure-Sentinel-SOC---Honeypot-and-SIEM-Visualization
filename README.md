# 🛡️ Active Directory Attack Lab (Based on Josh Madakor's Guide)

A hands-on security lab simulating real-world Active Directory (AD) attacks and defenses.  
This project follows [Josh Madakor's tutorial](https://www.youtube.com/watch?v=g5JL2RIbThM) and was extended to include post-exploitation, detection, and logging.

---

## ✅ Lab Overview

| Component         | Details                                |
|------------------|----------------------------------------|
| Domain Controller | Windows Server 2019 (AD + DNS)         |
| Victim Machine    | Windows 10 (Domain-joined)             |
| Attacker Machine  | Kali Linux                             |
| Tools Used        | Mimikatz, BloodHound, Rubeus, Impacket, PowerView, Splunk |

📘 **Setup instructions:** [docs/setup.md](./docs/setup.md)

---

## 🎯 Project Objectives

- 🛠️ Build an on-prem Active Directory environment in VirtualBox
- 💥 Simulate AD attacks (Kerberoasting, Pass-the-Hash, ACL Abuse)
- 🔍 Monitor attacker behavior via Windows Logs + Splunk
- 📚 Document attack steps, tools, and detection strategies

---

## ⚔️ Attacks Simulated

| Attack Technique   | Tool Used         | Goal                               |
|--------------------|------------------|------------------------------------|
| Kerberoasting      | Rubeus           | Crack service account password     |
| Pass-the-Hash      | Impacket (psexec.py) | Lateral movement                |
| Enumeration        | PowerView, BloodHound | Map domain access paths     |
| ACL Abuse          | BloodHound       | Privilege escalation to Domain Admin |

---

## 🔍 Detection & Logging

- Monitored key Event IDs: `4624` (Logon), `4769` (TGS Request), `4688` (Process Creation)
- Centralized log collection via **Splunk**
- Planned dashboards & search queries (coming soon)

---

## 🧠 Key Takeaways

- How attackers exploit misconfigured AD environments
- Importance of endpoint visibility & centralized logging
- Hands-on experience with real-world offensive security tools

---

## 📸 Screenshots

_(Coming soon – BloodHound graphs, terminal outputs, Splunk dashboards)_

---

## 📎 References

- [Josh Madakor’s YouTube Tutorial](https://www.youtube.com/watch?v=g5JL2RIbThM)
- [BloodHound](https://github.com/BloodHoundAD/BloodHound)
- [Impacket](https://github.com/SecureAuthCorp/impacket)
- [TryHackMe: Attacktive Directory](https://tryhackme.com/room/attacktivedirectory)

---

## 🔒 Disclaimer

This lab is intended for educational and ethical learning purposes only.
