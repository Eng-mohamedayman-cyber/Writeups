# 🔐 Privilege Escalation: SUID

you know that files can have read, write, and execute permissions. These are given to users within their privilege levels. This changes with SUID (Set-user Identification) and SGID (Set-group Identification). These allow files to be executed with the permission level of the file owner or the group owner

---

* **To find file with SUID permission you use this command :**

```bash
find / -type f -perm -4000 2>/dev/null
```
![img](screenshots/SUID/result_SUID.png)

* **we find base64 as SUID in owner user "rws"**

![img](screenshots/SUID/base64.png)

* **will use this bin to read shadow file and get copy from it**

![img](screenshots/SUID/base64_shadow.png)

* **make file and copy this hash**

![img](screenshots/SUID/file_hash.png)
![img](screenshots/SUID/hash_copy.png)

* **use john to undecription the hash of password**

![img](screenshots/SUID/john_get_passwd.png)

* **Now you can switch user**
```bash
su gerryconway
```

![img](screenshots/SUID/change_user.png)

* **find flag and read it by base64**

![img](screenshots/SUID/get_flag.png)


