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
if repated
Alternatively:

```bash
dirb http://<TARGET_IP>
```
---
