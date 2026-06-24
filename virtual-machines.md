# Virtual Machines

## Overview

Two Azure virtual machines were deployed within the **vnet-webapp-dev** Virtual Network to host the web application environment.

The deployment includes:

* One Ubuntu Linux virtual machine
* One Windows Server virtual machine

Both virtual machines reside in the same subnet and are administered securely using **Azure Bastion**, eliminating the need to expose SSH (22) or RDP (3389) directly to the internet.

---

# Linux Virtual Machine

The Linux VM was created with the following configuration.

| Property         | Value                                  |
| ---------------- | -------------------------------------- |
| Operating System | Ubuntu Server 22.04 LTS                |
| Size             | Standard_D2ls_v7                       |
| Authentication   | SSH Public Key                         |
| Virtual Network  | vnet-webapp-dev                        |
| Subnet           | subnet-webapp                          |
| Public IP        | None *(managed through Azure Bastion)* |

The VM serves as the Linux-based application server for the project.

---

# Windows Virtual Machine

The Windows VM was deployed for administrative and application hosting purposes.

| Property         | Value                                  |
| ---------------- | -------------------------------------- |
| Operating System | Windows Server 2022 Datacenter         |
| Size             | Standard_D2ls_v7                       |
| Authentication   | Username and Password                  |
| Virtual Network  | vnet-webapp-dev                        |
| Subnet           | subnet-webapp                          |
| Public IP        | None *(managed through Azure Bastion)* |

The VM provides a Windows environment for administration and application testing.

---

# Virtual Machine Networking

Both virtual machines were connected to the same Virtual Network.

```
vnet-webapp-dev
│
├── AzureBastionSubnet
│      └── Azure Bastion
│
└── subnet-webapp
       ├── Ubuntu VM
       └── Windows VM
```

This configuration enables secure communication between Azure resources while preventing direct administrative access from the public internet.

---

# Secure Administrative Access

Azure Bastion was configured to provide browser-based access to both virtual machines through the Azure Portal.

### Linux VM

Administrative access was successfully established using SSH over Azure Bastion.

Validation commands executed:

```bash
whoami
pwd
uname -a
ls -la
```

These commands confirmed successful authentication and normal operating system functionality.

---

### Windows VM

Administrative access was established using Remote Desktop over Azure Bastion.

After login, the following were verified:

* Windows desktop loaded successfully.
* Server Manager opened correctly.
* System Information was accessible.
* Administrative privileges were confirmed.

---

# Security Configuration

The virtual machines were deployed following Azure security best practices.

Implemented controls include:

* Azure Bastion for secure remote administration.
* No direct exposure of SSH (22) or RDP (3389) to the internet.
* Network Security Group (NSG) controlling network traffic.
* Virtual machines hosted within a private Virtual Network.

This approach significantly reduces the attack surface while maintaining secure administrative access.

---

# Validation

Deployment was validated through successful access to both virtual machines.

Validation results include:

* Ubuntu VM deployed successfully.
* Windows Server VM deployed successfully.
* Azure Bastion successfully connected to both virtual machines.
* Linux verification commands executed successfully.
* Windows desktop environment successfully accessed.

---

# Screenshots

Find screenshots is screenshots/ directory.
