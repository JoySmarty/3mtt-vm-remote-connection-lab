# Troubleshooting Guide

## Overview

During the deployment of the Azure infrastructure, several configuration issues were encountered. Each issue was investigated and resolved before validating the final environment.

---

# Issue 1: Network Security Group Association

### Problem

Initially, no Network Security Group was attached during virtual machine creation.

### Cause

The Azure Portal deployment wizard did not provide an option to associate an NSG directly with the virtual machine's network interface.

### Resolution

The NSG was associated with the virtual network subnet (`subnet-webapp`) after deployment. This allowed the security rules to apply to all virtual machines within the subnet.

---

# Issue 2: Windows Bastion Connection

### Problem

The Ubuntu virtual machine was successfully accessible through Azure Bastion, but the Windows virtual machine could not initially establish an RDP session.

### Investigation

The following items were verified:

* Virtual machine deployment status
* Azure Bastion deployment
* Virtual network configuration
* AzureBastionSubnet configuration
* NSG association
* Windows administrator credentials

### Resolution

After correcting the configuration and verifying the deployment, Azure Bastion successfully established a Remote Desktop session to the Windows virtual machine.

Both Linux and Windows virtual machines were subsequently accessible through Azure Bastion.

---

# Issue 3: Secure Remote Administration

### Problem

Direct administrative access using public IP addresses was not desired due to security best practices.

### Resolution

Azure Bastion was deployed to provide secure browser-based administration.

Successful validation included:

### Ubuntu Linux

```bash
whoami
pwd
uname -a
ls -la
```

### Windows Server

* Successful Remote Desktop session
* Windows desktop loaded successfully
* Server Manager accessible
* Administrative access confirmed

---

# Final Validation

The completed environment was validated by confirming:

* Resource Group deployed successfully.
* Virtual Network and subnets configured correctly.
* Network Security Group associated with the subnet.
* Azure Bastion deployed successfully.
* Ubuntu virtual machine accessible through SSH via Azure Bastion.
* Windows Server virtual machine accessible through RDP via Azure Bastion.
* Linux verification commands executed successfully.

The environment met the project objectives by providing secure administration without exposing SSH or RDP directly to the public internet.

---

# Lessons Learned

Key takeaways from this project include:

* Azure Bastion provides secure remote administration without requiring public IP addresses on virtual machines.
* Network Security Groups should be associated with the appropriate subnet or network interface to enforce security policies.
* AzureBastionSubnet must be created with the required name before deploying Azure Bastion.
* Validating connectivity after deployment helps identify configuration issues early and ensures all components function as expected.

