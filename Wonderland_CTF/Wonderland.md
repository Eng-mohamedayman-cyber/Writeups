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

