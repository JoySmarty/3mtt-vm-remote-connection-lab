# Networking Configuration

## Overview

Networking is a fundamental component of Azure Infrastructure-as-a-Service (IaaS). In this project, a Virtual Network (VNet) was created to provide secure communication between Azure resources. The network includes a default subnet for the virtual machines and a dedicated AzureBastionSubnet required for Azure Bastion deployment.

A Network Security Group (NSG) was configured to manage inbound and outbound traffic while Azure Bastion provided secure browser-based administrative access.

---

# Virtual Network Configuration

The Virtual Network was configured with the following settings:

| Property      | Value                |
| ------------- | -------------------- |
| Name          | **vnet-webapp-dev**  |
| Region        | East US              |
| Address Space | **10.0.0.0/16**      |

The Virtual Network provides a private network where Azure resources can securely communicate with one another.

---

# Subnet Configuration

Two subnets were created within the Virtual Network.

## Default Subnet

This subnet hosts both the Linux and Windows virtual machines.

| Property      | Value           |
| ------------- | --------------- |
| Name          | subnet-webapp   |
| Address Range | **10.0.1.0/24** |

---

## Azure Bastion Subnet

Azure Bastion requires a dedicated subnet named **AzureBastionSubnet**. This subnet is reserved exclusively for the Bastion service and cannot host virtual machines or other Azure resources.

| Property      | Value              |
| ------------- | ------------------ |
| Name          | AzureBastionSubnet |
| Address Range | **10.0.2.0/26**    |

The subnet name **AzureBastionSubnet** is mandatory for successful Azure Bastion deployment.

---

# Network Security Group (NSG)

A Network Security Group (NSG) was configured to control inbound and outbound network traffic for the virtual machines.

The NSG acts as a virtual firewall, allowing only authorized traffic to reach Azure resources.

---

# Security Rules

Administrative access to the virtual machines was performed through Azure Bastion. As a result, direct exposure of management ports to the internet was avoided.

The security configuration included:

* Azure Bastion for secure browser-based access.
* Restricted administrative access.
* Private communication within the Virtual Network.
* Controlled inbound traffic using NSG rules.

---

# Remote Management

Remote administration was successfully performed using Azure Bastion.

### Linux Virtual Machine

* Browser-based SSH session established.
* Successfully authenticated using SSH credentials.
* Executed verification commands:

  * `whoami`
  * `pwd`
  * `uname -a`
  * `ls -la` 

### Windows Virtual Machine

* Browser-based Remote Desktop session established.
* Successfully authenticated using administrator credentials.
* Verified desktop environment.
* Opened Server Manager and System Information.

---

# Network Flow

The following diagram illustrates how secure administrative access is provided.

```text
                Administrator
                      │
             Azure Portal (HTTPS)
                      │
              Azure Bastion Host
                      │
        ┌─────────────┴─────────────┐
        │                           │
 Ubuntu Server VM            Windows Server VM
        │                           │
        └─────────────┬─────────────┘
                      │
            Default Subnet
              10.0.1.0/24
                      │
           Virtual Network
             10.0.0.0/16
                      │
         AzureBastionSubnet
            10.0.2.0/26
```

---

# Security Best Practices Implemented

The networking configuration follows Azure security recommendations by:

* Using Azure Bastion instead of exposing SSH (22) and RDP (3389) directly to the internet.
* Isolating Azure Bastion in its dedicated subnet.
* Restricting administrative access to authenticated Azure portal users.
* Keeping virtual machines within a private virtual network.
* Applying Network Security Groups to regulate network traffic.

These measures reduce the attack surface while maintaining secure administrative access.

---

# Validation

The networking configuration was validated through successful remote access to both virtual machines using Azure Bastion.

Validation included:

* Successful SSH connection to the Linux VM.
* Successful Remote Desktop connection to the Windows VM.
* Verification that both VMs were reachable through the Virtual Network.
* Successful execution of administrative tasks after login.

---

# Screenshots

Find screenshots in the screenshots/ directory.
