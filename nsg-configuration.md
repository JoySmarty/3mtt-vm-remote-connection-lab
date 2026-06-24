# Network Security Group (NSG) Configuration


# Network Security Group (NSG) Configuration

## Overview

A Network Security Group (NSG) was configured to control network traffic within the Azure environment. The NSG acts as a virtual firewall by allowing or denying inbound and outbound traffic based on defined security rules.

The NSG was associated with the virtual machine subnet to provide centralized traffic filtering for both the Linux and Windows virtual machines.

## 📌 Purpose

NSGs control inbound and outbound traffic to Azure Virtual Machines.

---

## 🔐 Inbound Rules Configured

| Priority | Port | Name | Purpose |
|----------|------|------|--------|
| 100 | 22 | SSH | Linux VM access |
| 200 | 3389 | RDP | Windows VM access |

---

## 🛡️ Security Configuration

- Source restricted to **My IP address**
- No open public access (0.0.0.0/0 avoided)
- Only required ports enabled

---

# NSG Details

| Property        | Value                  |
| --------------- | ---------------------- |
| Resource Type   | Network Security Group |
| Associated With | subnet-webapp          |
| Virtual Network | vnet-webapp-dev        |
| Region          | East US                |

The NSG protects resources deployed within the subnet by evaluating traffic against its configured security rules.

---

# Security Configuration

Administrative access to the virtual machines was provided through Azure Bastion rather than exposing management ports directly to the internet.

The security design included:

* Azure Bastion for browser-based administration.
* NSG associated with the subnet.
* Virtual machines deployed without public IP addresses.
* Internal communication restricted to the virtual network.

This configuration follows Azure security best practices by minimizing the public attack surface.

---

# Azure Bastion Integration

Azure Bastion enables secure remote management over HTTPS through the Azure Portal.

Using Bastion:

* Linux VM was accessed through SSH.
* Windows VM was accessed through Remote Desktop (RDP).
* No direct inbound SSH (22) or RDP (3389) access from the internet was required.

---

# Validation

The NSG configuration was validated by successfully accessing both virtual machines through Azure Bastion.

Validation included:

* Successful SSH connection to the Ubuntu VM.
* Successful RDP connection to the Windows Server VM.
* Successful execution of Linux verification commands:

  * `whoami`
  * `pwd`
  * `uname -a`
  * `ls -la`

---

## 📌 Summary

NSGs act as a virtual firewall ensuring only authorized traffic reaches the virtual machines.