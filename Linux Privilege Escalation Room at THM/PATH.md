# 🔐 Privilege Escalation: PATH

If a folder for which your user has write permission is located in the path, you could potentially hijack an application to run a script. PATH in Linux is an environmental variable that tells the operating system where to search for executables. For any command that is not built into the shell or that is not defined with an absolute path, Linux will start searching in folders defined under PATH. (PATH is the environmental variable we're talking about here, path is the location of a file).

---

if you want to know any variable you write: " echo $<variable> "
```bash
echo $PATH
```
![img](screenshots/PATH/normal_path.png)

---
then to change this variable "PATH" to start open file from i want :

```bash
export PATH=/tmp:$PATH
```

![img](screenshots/PATH/new_path.png)
