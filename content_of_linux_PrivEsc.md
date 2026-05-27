# 🐧 Linux Privilege Escalation Walkthroughs & Cheat Sheets

Welcome to my comprehensive Linux Privilege Escalation repository. This project documents step-by-step walkthroughs, technical concepts, and exploitation methodologies for various local privilege escalation vectors encountered during labs (such as TryHackMe and HackTheBox) and security assessments.

Each section includes clear technical theory, command references, and visual proof-of-concept (PoC) screenshots.

---

## 📂 Table of Contents

Click on any of the interactive links below to navigate to the specific exploitation technique writeup:

*   [🔍 System Enumeration](./Enumeration.md) — Understanding automated auditing and manual scanning strategies.
*   [💾 Kernel Exploitation](./Kernel_Exploit.md) — Abusing outdated kernel versions and compiling local exploits via `gcc` to gain instant root shells.
*   [🔑 Sudo Misconfigurations](./Sudo.md) — Leveraging application execution rights via `sudo -l` to escape restricted environments (e.g., `nano`, `less`, `find`).
*   [🔐 SUID Binaries](./SUID.md) — Exploiting special file permissions on binaries like `base64` to read sensitive configuration files and crack hashes.
*   [🎯 Linux Capabilities](./Capabilities.md) — Abusing process privileges like `cap_setuid+ep` assigned to standard binaries (`vim`, `view`) to spawn root shells.
*   [⏳ Cron Jobs Hijacking](./Cron_Job.md) — Exploiting wildcard misconfigurations or world-writable scripts executed automatically by the root cron daemon.
*   [🛣️ PATH Hijacking](./PATH_Hijacking.md) — Manipulating the system environment `$PATH` variable to redirect binary execution to malicious scripts inside `/tmp`.
*   [🌐 Network File Sharing (NFS)](./Network_File_Sharing.md) — Mounting remote shares and abusing the `no_root_squash` directive to inject SUID C binaries.

---

## 🛠️ Global Tools & Key References

Throughout these writeups, the following industry-standard auditing tools and references were utilized:

*   **Automated Auditing:** `LinPeas.sh` & `LinEnum.sh` (Automated Enumeration scripts).
*   **Binary Exploitation Reference:** [GTFOBins Official Portal](https://github.io) (The ultimate Unix binary escape index).
*   **Offline Password Cracking:** `John the Ripper` powered by the `rockyou.txt` wordlist.

---

## 💡 Methodology Note

Effective Linux privilege escalation always follows a structured lifecycle:
1. **Automated Scanning:** Quick scanning for low-hanging fruits using tools like LinPeas.
2. **Manual Enumeration:** Diving deep into target system configurations, environment paths, internal networking ports, and user context.
3. **Exploitation:** Finding or building the precise proof-of-concept (PoC) vector.
4. **Cleanup:** Working out of volatile directories like `/tmp` to support anti-forensics and preserve system stability.

---
*Disclaimer: The materials and documentation within this repository are for educational, training, and authorized security auditing purposes only.*
