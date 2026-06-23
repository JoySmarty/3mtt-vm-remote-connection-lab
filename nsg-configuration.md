# Network Security Group (NSG) Configuration

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

## 📌 Summary

NSGs act as a virtual firewall ensuring only authorized traffic reaches the virtual machines.