# 3mtt-vm-remote-connection

# Azure Virtual Machine Remote Connectivity Lab

## Project Overview

This project demonstrates the deployment and secure remote management of Linux and Windows virtual machines in Microsoft Azure using **Azure Bastion**. The environment was designed following Azure networking and security best practices by allowing administrative access without exposing Remote Desktop Protocol (RDP) or Secure Shell (SSH) directly to the internet.

The project includes the creation of a virtual network, subnets, network security groups (NSGs), Azure Bastion, and two virtual machines running Ubuntu Server and Windows Server. Remote connectivity was successfully verified through Azure Bastion for both operating systems.

---

# Objectives

The objectives of this project were to:

* Deploy a Linux virtual machine in Microsoft Azure.
* Deploy a Windows virtual machine in Microsoft Azure.
* Configure a Virtual Network (VNet) and subnets.
* Deploy Azure Bastion for secure remote administration.
* Configure Network Security Groups (NSGs) to control network traffic.
* Verify successful remote access to both virtual machines.
* Demonstrate basic command execution and system verification.
* Apply Azure security best practices by avoiding direct public management access.

---

# Architecture

The deployed environment consists of:

* Resource Group
* Virtual Network
* Default subnet for virtual machines
* AzureBastionSubnet
* Azure Bastion Host
* Linux Virtual Machine
* Windows Virtual Machine
* Network Security Group

```
                    Internet
                        │
                  HTTPS (443)
                        │
                 Azure Bastion
                        │
        ┌───────────────┴───────────────┐
        │                               │
 Ubuntu Linux VM                 Windows Server VM
        │                               │
        └───────────────┬───────────────┘
                        │
              Virtual Network (VNet)
```

---

# Azure Resources

| Resource                | Purpose                                    |
| ----------------------- | ------------------------------------------ |
| Resource Group          | Logical container for Azure resources      |
| Virtual Network         | Private network for both virtual machines  |
| Default Subnet          | Hosts Linux and Windows virtual machines   |
| AzureBastionSubnet      | Dedicated subnet required by Azure Bastion |
| Azure Bastion           | Secure browser-based SSH and RDP access    |
| Linux Virtual Machine   | Ubuntu Server for SSH testing              |
| Windows Virtual Machine | Windows Server for RDP testing             |
| Network Security Group  | Controls inbound and outbound traffic      |

---

# Networking Configuration

| Component                     | Configuration           |
| ----------------------------- | ----------------------- |
| Virtual Network Address Space | 10.0.0.0/16             |
| Default Subnet                | 10.0.1.0/24             |
| AzureBastionSubnet            | 10.0.2.0/26             |
| Remote Access                 | Azure Bastion           |
| Administrative Protocols      | SSH and RDP via Bastion |

---

# Virtual Machines

## Linux VM

* Ubuntu Server LTS
* Standard SSD Managed Disk
* SSH authentication
* Connected through Azure Bastion

Verification commands executed:

```bash
whoami
uname -a
hostname
pwd
ls
```

---

## Windows VM

* Windows Server
* Standard SSD Managed Disk
* Username and password authentication
* Connected through Azure Bastion using browser-based Remote Desktop

Verification included:

* Successful desktop login
* System Information
* File Explorer access
* Server Manager launch

---

# Azure Bastion Deployment

Azure Bastion was deployed to provide secure browser-based access to both virtual machines without exposing SSH (22) or RDP (3389) directly to the internet.

Deployment included:

* Creation of the required **AzureBastionSubnet**
* Deployment of an Azure Bastion Host
* Browser-based SSH session to the Linux VM
* Browser-based RDP session to the Windows VM
* Successful authentication to both machines

This implementation follows Microsoft's recommended approach for securely managing Azure virtual machines.

---

# Security Considerations

The project follows several Azure security best practices:

* Administrative access is provided through Azure Bastion.
* Direct SSH and RDP exposure to the public internet is avoided.
* Network Security Groups restrict inbound traffic.
* Virtual machines communicate within a private virtual network.
* Standard SSD managed disks provide encrypted Azure-managed storage.

---

# Validation

The deployment was successfully validated by:

### Linux VM

* Successful Bastion connection
* Successful authentication
* Execution of:

  * `whoami`
  * `uname -a`
  * `hostname`

### Windows VM

* Successful Bastion connection
* Successful authentication
* Desktop access confirmed
* System Information verified

---

# Screenshots

The repository contains screenshots demonstrating:

* Azure Resource Group
* Virtual Network configuration
* Azure Bastion deployment
* AzureBastionSubnet
* Linux VM Overview
* Windows VM Overview
* Linux Bastion SSH session
* Windows Bastion RDP session
* Network Security Group configuration

---

# Cost Management

Azure Bastion is a billable service. After completing testing and validation, all Azure resources were deleted to avoid unnecessary charges.

---

# Learning Outcomes

This project provided practical experience with:

* Microsoft Azure Virtual Machines
* Azure Virtual Networks
* Network Security Groups
* Azure Bastion
* Linux administration
* Windows Server administration
* Secure remote connectivity
* Azure resource management
* Cloud networking best practices

---

# Repository Structure

```
.
├── README.md
├── architecture.md
├── networking.md
├── azure-bastion.md
├── linux-vm.md
├── windows-vm.md
├── troubleshooting.md
└── screenshots/
```

---
# 🚀 Project Cleanup

All resources were deleted after testing using Resource Group deletion to prevent additional costs.

---
# 📌 Author

Cloud & DevOps Learning Project (3MTT)


---