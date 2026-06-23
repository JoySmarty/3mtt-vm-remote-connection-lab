# 3mtt-vm-remote-connection-lab

# Azure VM Remote Connection Lab

## 📌 Project Overview

This project demonstrates how to deploy, configure, and securely access Azure Virtual Machines using both Windows (RDP) and Linux (SSH).

It focuses on core cloud computing and DevOps fundamentals such as virtual networking, remote access, and security configuration.

---

## 🎯 Objectives

- Deploy Azure Virtual Machines (Windows & Linux)
- Configure Virtual Networks and Subnets
- Set up Network Security Groups (NSGs)
- Establish secure remote connections using SSH and RDP
- Apply cloud security best practices
- Perform basic system verification and troubleshooting

---

## 🏗️ Azure Architecture

The architecture consists of:

- Resource Group
- Virtual Network (VNet)
- Subnet
- Network Security Group (NSG)
- Public IP Address
- Windows VM (RDP access)
- Linux VM (SSH access)

📌 Architecture Diagram:
![Architecture](screenshots/architecture-diagram.png)

---

## 💻 Virtual Machines Deployed

### 🟢 Linux VM
- Name: `vm-webapp-dev-linux`
- OS: Ubuntu Linux
- Access: SSH (Port 22)

### 🟠 Windows VM
- Name: `vm-webapp-dev-eastus-win-01`
- OS: Windows Server
- Access: RDP (Port 3389)

---

## 🔐 Network Security Configuration

Network Security Groups were configured to control inbound traffic:

| Port | Protocol | Purpose |
|------|----------|--------|
| 22   | TCP      | SSH (Linux VM) |
| 3389 | TCP      | RDP (Windows VM) |

Security was enhanced by restricting access to:
- My public IP address only

---

## 🔗 Remote Access Methods

### Linux VM (SSH)
```bash
ssh azureuser@<public-ip>

Windows VM (RDP)
Connected using Remote Desktop Connection
Logged in using administrator credentials
🧪 System Verification

On Linux VM:

whoami
ls
uname -a

On Windows VM:

File Explorer navigation
System Information (msinfo32)
🔒 Security Best Practices Applied
Restricted inbound NSG rules to specific IPs
Used authentication-based access (SSH keys / passwords)
Closed unnecessary ports after testing
Deleted resources after completion to avoid cost
📸 Screenshots

See /screenshots folder for:

VM overview
SSH connection
RDP connection
NSG rules
System information
Architecture diagram
🧠 Key Learnings
Azure virtual networking fundamentals
Secure remote server administration
Difference between SSH and RDP
Importance of NSG rules in cloud security
Real-world DevOps VM lifecycle management
🚀 Project Cleanup

All resources were deleted after testing using Resource Group deletion to prevent additional costs.

📌 Author

Cloud & DevOps Learning Project (3MTT)


---