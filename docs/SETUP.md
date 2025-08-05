# 🛡️ Active Directory Attack Lab

> 🧪 Based on TCM Security's "Windows Active Directory Lab" setup

## 1️⃣ Lab Requirements

- [VirtualBox](https://www.virtualbox.org/)
- Windows Server 2019 ISO
- Windows 10 ISO
- Kali Linux ISO

## 2️⃣ VM Configuration

### 🖥️ Windows Server 2019 (DC01)
- Hostname: `DC01`
- IP: `192.168.10.10`
- Role: Domain Controller
- Domain: `offense.local`

### 🧑‍💻 Windows 10 Client (Win10)
- Hostname: `Win10`
- Joined to domain `offense.local`

### 🐉 Kali Linux (Attacker)
- Suggested Tools:
  - `impacket`
  - `bloodhound`
  - `kerbrute`
  - `crackmapexec`
  - `evil-winrm`

## 3️⃣ Domain Configuration

- Promote `DC01` as Domain Controller
- Enable RDP & SMB
- Create test users:
  - `jdoe`, `svcadmin`, etc.
- Set weak passwords (`P@ssw0rd!`)

## 4️⃣ Attack Scenarios

- 🎯 Kerberoasting with `GetUserSPNs.py`
- 🧨 AS-REP Roasting
- 🔐 Dump NTLM hashes via `secretsdump.py`
- 🪪 Pass-the-Hash with `psexec.py`
- 🧭 Enumeration with BloodHound

## 5️⃣ Notes

- All VMs on **Internal Network**: `10.10.10.0/24`
- Password used: `P@ssw0rd!` (for demonstration purposes only)
- Optional: Enable snapshots for quick lab resets
