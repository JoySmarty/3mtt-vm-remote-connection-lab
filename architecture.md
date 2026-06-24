# Azure Architecture Overview

## Overview

This project implements a secure Azure infrastructure for deploying and managing Linux and Windows virtual machines. The environment uses Azure networking services and Azure Bastion to provide secure browser-based administrative access without exposing management ports directly to the public internet.

The architecture demonstrates core Infrastructure-as-a-Service (IaaS) concepts, including virtual networking, subnetting, network security, and secure remote management.

---

# Architecture Components

The solution consists of the following Azure resources:

| Azure Resource               | Purpose                                               |
| ---------------------------- | ----------------------------------------------------- |
| Resource Group               | Logical container for all project resources           |
| Virtual Network (VNet)       | Private network for Azure resources                   |
| Default Subnet               | Hosts the Linux and Windows virtual machines          |
| AzureBastionSubnet           | Dedicated subnet required for Azure Bastion           |
| Azure Bastion                | Secure browser-based SSH and RDP connectivity         |
| Linux Virtual Machine        | Ubuntu Server used for SSH administration             |
| Windows Virtual Machine      | Windows Server used for Remote Desktop administration |
| Network Security Group (NSG) | Controls inbound and outbound network traffic         |

---

# Network Layout

The environment uses a single Virtual Network with two subnets.

| Component          | Configuration |
| ------------------ | ------------- |
| Address Space      | 10.0.0.0/16   |
| Default Subnet     | 10.0.1.0/24   |
| AzureBastionSubnet | 10.0.2.0/26   |

The dedicated **AzureBastionSubnet** is required by Microsoft Azure and must be named exactly **AzureBastionSubnet** for Azure Bastion deployment.

---

# Architecture Diagram

```text
                         Internet
                             │
                      HTTPS (TCP 443)
                             │
                     Azure Bastion Host
                             │
        ┌────────────────────┴────────────────────┐
        │                                         │
   Ubuntu Server VM                        Windows Server VM
        │                                         │
        └────────────────────┬────────────────────┘
                             │
                     Default Subnet
                       10.0.1.0/24
                             │
                 Virtual Network (VNet)
                      10.0.0.0/16
                             │
                 AzureBastionSubnet
                      10.0.2.0/26
```

---

# Traffic Flow

The following sequence describes how administrators securely connect to the virtual machines:

1. The administrator signs in to the Azure portal.
2. Azure Bastion establishes a secure HTTPS (TCP 443) session.
3. Azure Bastion communicates with the target virtual machine over the private virtual network.
4. The administrator gains browser-based access without exposing SSH (TCP 22) or RDP (TCP 3389) directly to the internet.

This approach significantly reduces the attack surface compared to exposing management ports through public IP addresses.

---

# Network Security

Network Security Groups (NSGs) were configured to control inbound traffic to the virtual machines.

Security measures implemented include:

* Restricting inbound management traffic.
* Using Azure Bastion instead of direct public access.
* Keeping administrative communication within the Azure Virtual Network.
* Following Azure's recommended secure remote management practices.

---

# Azure Bastion Architecture

Azure Bastion acts as a managed jump host within the Azure Virtual Network.

Key characteristics include:

* Browser-based SSH and RDP access.
* No VPN required.
* No direct exposure of management ports.
* Centralized and secure administrative access.
* Integration with the Azure portal.

---

# Benefits of the Architecture

This design provides several advantages:

* Improved security by avoiding direct exposure of SSH and RDP.
* Centralized management through Azure Bastion.
* Segregation of network resources using dedicated subnets.
* Compliance with Azure networking best practices.
* Simplified administration of Linux and Windows virtual machines.

---


