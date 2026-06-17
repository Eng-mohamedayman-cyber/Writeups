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

```
dirb URL_of_Target
```

![img](Screenshots/)



