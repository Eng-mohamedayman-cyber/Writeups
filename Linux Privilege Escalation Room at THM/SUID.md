# 🔐 Privilege Escalation: SUID

you know that files can have read, write, and execute permissions. These are given to users within their privilege levels. This changes with SUID (Set-user Identification) and SGID (Set-group Identification). These allow files to be executed with the permission level of the file owner or the group owner

---

* **To find file with SUID permission you use this command :**
  find / -type f -perm -4000 2>/dev/null
