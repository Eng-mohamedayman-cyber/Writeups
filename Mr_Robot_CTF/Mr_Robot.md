##Mr Robot CTF : https://tryhackme.com/room/mrrobot

---

start with scan the IP using Nmap :
we found 3 port open :

* *22 --> ssh*
* *80 --> http*
* *443 --> https*

![img](Screenshots/)

get the ip and open the firefox browser, and if can get any useful thing

we find only record message and videos

![img](Screenshots/)

find subdomans of this ip :
we many methods to find subdomans :

1- using "drib"

```bash
dirb URL_of_Target
```

![img](Screenshots/)

you can also use gobuster 

after finding subdomains search in it to find any useful thing to use:

we find many usefull domain :

login-page: in it when we write username and password it response if user valid or invalid

![img](Screenshots/)

robot : in this subdomain we find first key(flag) and a list can use to make brute force in login page
license : find in it hash "ZWxsaW90OkVSMjgtMDY1Mgo="

![img](Screenshots/)

the hash --> I knew that is encryption by "base64" because the text ends with an equals sign (=), which is the distinctive symbol used as padding in the Base64 encoding system when the text isn’t divisible by 3 bytes.

decoding it
```bash
echo "ZWxsaW90OkVSMjgtMDY1Mgo=" | base64 -d
```

![img](Screenshots/)

the result is amazing I am get user and password --> when i try it login as admin

![img](Screenshots/)

then we have an admin permission so we can go directly to appearance editor theme because :

* Direct Code Execution: WordPress allows Admins to edit .php files directly, letting us run system commands on the server.
* Predictable File Paths: Themes use known directories (wp-content/themes/), making our reverse shell easy to find and trigger.
* Safe Stealth Trigger: Modifying 404.php executes the shell via any broken link without breaking the website.

![img](Screenshots/)

now write a reverse shell can make connect by it to the server 
you can find a reverse shell code in the kali at path : /usr/share/webshells/php/php-reverse-shell.php
```bash
cat /usr/share/webshells/php/php-reverse-shell.php
```

copy it and paste in 404.php
then change the ip and port to connected

![img](Screenshots/)

now use netcat 
```bash
sudo nc -nlvp <port>
```

![img](Screenshots/)

when go in the server we try to make a privilege escalation and get root permission 
try by "sudo -l" but not find any thing
try with SUID 
```bash
find / -type f -perm -4000 2>/dev/null
```

find nmap used as SUID so :
```bash
nmap --interaction
!sh
python -c'import pty ; pty.spawn("/bin/bash")'
```
this line " python -c'import pty ; pty.spawn("/bin/bash")' " to appear the command shell

![img](Screenshots/)

you have now a root privilege search to the keys(falgs)


