# Intro
- Alright for the previous part my colleague just showed you the main functionalities of sqlmap, now I will show you the extended capabilities of sqlmap
---
- these include the file system access and operating system access gained through effectively tapping into the database management systems vulnerability
---
- During any penetration test it can be very useful to have access to files on the compromised machine, as it can further lead to disclosure of information that helps the attacker to retrieve sensitive information.
	- So to start File System Access, the session user must have the privileges of "FILE" and "CREATE TABLE", so we can run the command: 
```bash
mysql -u "target-url" -privileges 
```
- This will show us all the privileges of the database users. 
- OK now that we have checked to see what privileges our users have, we can now start hacking.
- I will be using the website provided by sqli-labs, so we will get its URL, and paste it into here to perform the SQL injection.
	- and I will put the `file-read` switch to fetch a file from the target:
```bash
sqlmap -u "http example.com/page.php?id=1" file-read /path/to/index.php
```
- and as expected, you can see it is downloaded to this location.
---
- Now we will move on to the part of operating system takeover
- so the first command I will showcase is `--os-cmd` which can execute commands on the target machine
- The way it does this is it first uploads a payload which establishes a connection between the target and us
- so here is the command:
```bash
sqlmap -u <target url> os-cmd=""
```
---
- Now if you thought that was impressive, you will be even more with the next switch.
- Now we will move on to an even more powerful functionality which is the `--os-shell` switch that provides an interactive shell directly to the target operating system.
- so here is the command:
```bash
sqlmap -u <target url> --os-shell
```
- so here I will list the files:`ls`
- and if you still don't believe me, here's me creating a file in the targets file system.
```bash
os-shell> touch ali
```
- and that... was all about sqlmap, any questions?