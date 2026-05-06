<h1 align="center">🔐 Linux Privilege Escalation</h1>
<h3 align="center">TryHackMe Room Writeup</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-TryHackMe-red?style=for-the-badge&logo=tryhackme">
  <img src="https://img.shields.io/badge/Category-Privilege%20Escalation-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/OS-Linux-yellow?style=for-the-badge&logo=linux">
</p>

---

## 📌 Overview

This writeup covers the concept of **Privilege Escalation** in Linux systems, as introduced in the TryHackMe room.
It focuses on understanding the importance of escalating privileges after gaining initial access.

---

## 🔐 What is Privilege Escalation?

Privilege Escalation is the process of gaining higher permissions than those initially assigned.

> In simple terms: moving from a low-privileged user ➜ root (administrator)

### 🧪 Technically:

It involves exploiting:

* Vulnerabilities
* Misconfigurations
* Design flaws

This allows access to restricted system resources.

---

## ⚠️ Why is it Important?

In real-world penetration testing, initial access (**foothold**) rarely provides admin privileges.

Privilege Escalation is essential to gain **full system control**.

### 🚀 With elevated privileges, you can:

* 🔑 Reset passwords
* 🔓 Bypass access controls
* 🛠 Modify configurations
* 📌 Maintain persistence
* 👤 Manage user accounts
* ⚡ Execute administrative commands

---

## 🧠 Key Takeaway

> Without privilege escalation → Limited access
> With privilege escalation → Full system compromise

---

## 🧾 Notes

* Privilege Escalation is a **post-exploitation phase**
* Always check for:

  * SUID binaries
  * Misconfigured services
  * Weak permissions
  * Kernel exploits

---

## 📚 Next Steps

* Practice Linux PrivEsc rooms on TryHackMe
* Learn common enumeration tools:

  * `linpeas`
  * `linenum`
  * `ps`, `sudo -l`, `find`

---

## 👨‍💻 Author

**Mohamed**
Cybersecurity Learner | Penetration Testing Enthusiast
