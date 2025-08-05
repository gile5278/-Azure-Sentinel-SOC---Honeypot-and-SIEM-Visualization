# Active Directory Attack Lab Setup

> Guide based on TCM Security's YouTube video.

## 🧰 1. Lab Requirements

- VirtualBox
- Windows Server 2019 ISO
- Windows 10 ISO
- Kali Linux ISO

## 🖥️ 2. Virtual Machine Setup

### 2.1 Windows Server 2019
- Hostname: `DC01`
- IP Address: `192.168.10.10`
- Domain Name: `offense.local`

### 2.2 Windows 10 Client
- Hostname: `Win10`
- Domain Joined to `offense.local`

### 2.3 Kali Linux
- Installed tools: `impacket`, `bloodhound`, `kerbrute`, etc.

## 🔁 3. Domain Configuration

- Promote `DC01` to domain controller
- Create AD users:
  - `jdoe`, `svcadmin`, etc.
- Enable RDP, SMB

## 💣 4. Attack Scenarios

- Kerberoasting using `GetUserSPNs.py`
- AS-REP roasting
- NTLM hash dump with secretsdump
- Pass-the-Hash attack with `psexec.py`

## 📌 Notes

- Network settings: All VMs are on internal network `10.10.10.0/24`
- Passwords used: `P@ssw0rd!`

