# Troubleshooting Guide

## ❌ SSH Key Issues

### Problem:
Permission denied (publickey)

### Cause:
Incorrect or missing SSH key path

### Solution:
Use correct Git Bash path format:

```bash
ssh -i /c/Users/user/Downloads/key.pem azureuser@<public-ip>


❌ RDP Connection Issues
Problem:

Cannot connect to Windows VM

Solution:
Ensure port 3389 is open in NSG
Confirm Public IP is correct
Verify username and password
❌ NSG Blocking Access
Solution:
Set Source = My IP
Avoid using "Any" for production-like security
🧠 Lessons Learned
SSH requires correct private key path formatting
NSG misconfiguration is the most common issue
Azure networking is strict by default