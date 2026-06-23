# Azure Architecture Overview

## 📌 Architecture Components

This project is built using the following Azure services:

- Resource Group
- Virtual Network (VNet)
- Subnet
- Network Security Group (NSG)
- Public IP Address
- Virtual Machines (Linux & Windows)

---

## 🏗️ Architecture Diagram

![Architecture Diagram](screenshots/architecture-diagram.png)

---

## 🔄 Flow Overview

1. User connects via SSH or RDP
2. Traffic passes through NSG rules
3. Public IP routes request to VM
4. VM responds within secure subnet

---

## 🧠 Explanation

The architecture demonstrates secure cloud networking principles using Azure infrastructure components.