# 🔐 Privilege Escalation: Capabilities

Capabilities help manage privileges at a more granular level. For example, if the SOC analyst needs to use a tool that needs to initiate socket connections, a regular user would not be able to do that. If the system administrator does not want to give this user higher privileges, they can change the capabilities of the binary. As a result, the binary would get through its task without needing a higher privilege user
* **the command used to find capabilities is:**
```bash
getcap -r / 2>/dev/null
```
