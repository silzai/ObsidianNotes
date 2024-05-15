# Environment Setup:
- For hacking the sqli-labs and DVWA website, the setup is explained below: 
- We have to download three things, xampp server 5.6.39 for Linux and sqli-labs and DVWA website.
- First download and install xampp server version 5.6.39 on the victim machine. The version must be 5.6.39 as we want to download a php version that is vulnerable (as latest versions are relatively secure) and also because the website we will hack (sqli-labs) uses an older php version \[1].
	![[Pasted image 20240419212656.png]]
- Click on "XAMPP Linux" and click on "5.6.39" to download it.
	![[Pasted image 20240419212818.png]]
- Then run the installer and click "forward" on the default settings.
- note: the server will be downloaded to `/opt/`
- Now download sqli-labs from github \[2] as follows, and unzip/extract it.
	![[Pasted image 20240419213635.png]]
- Next download DVWA from their github website like so, and also extract it:
	![[Pasted image 20240420185507.png]]
- Now copy the sqli-labs and DVWA folders that was extracted to `/opt/lampp/htdocs/`
	![[Pasted image 20240419213857.png]]
- setting up xampp server is very easy, just "start" the services "Apache Web Server" and "MySQL Database" as shown below:
	![[Pasted image 20240419214231.png]]
- Now go to the sqli-labs website and press on "reset database":
	![[Pasted image 20240419214439.png]]
- The expected output after doing this will be:
	![[Pasted image 20240419214639.png]]
- Finally we have to give permissions to `/opt/lampp/htdocs` for File/Operating system access.
	![[Pasted image 20240419214523.png]]
- Now setup is complete, and we can hack sqli-labs.
# File System Access:
Modern database management systems often allow reading and writing files from the file system, which can be exploited through SQL injection vulnerabilities. SQLMap can be leveraged to perform file operations.
## Checking File Privileges:
- Use `privileges` switch to check if the DBMS user has file privileges.
- Example command: 
```sh
sqlmap -u "http://example.com/page.php?id=1" –privileges
```
- Here is the command output:
	![[Pasted image 20240419220949.png]]
## Reading Files:
- Use `file-read` switch followed by the full path of the file to read.
- Example command: 
```sh
sqlmap -u "http://example.com/page.php?id=1" --file-read /path/to/index.php
```
- SQLMap can download and save the file for later usage.
- Here is the command:
	![[Pasted image 20240419221340.png]]
- And here it is showing the download location:
	![[Pasted image 20240419221458.png]]
- As expected, when we go to that location, it is visible:
	![[Pasted image 20240419221711.png]]
## Considerations:
- Ensure proper file permissions and user privileges for successful file operations.
- Be mindful of file size limitations based on web server configurations.
- For Apache HTTPD, the default maximum URL length is 8 kilobytes.

SQLMap's file reading and writing capabilities can be powerful tools in the hands of a penetration tester. By exploiting SQL injection vulnerabilities, testers can gain access to sensitive files and even upload backdoor shells for further exploitation. However, it's crucial to understand the target system's configurations and limitations to execute these operations successfully.
# Operating System Access:
## Introduction
Now we will explore how to execute system commands on a target operating system using SQLMap.
## Overview of Operating System Takeover
SQLMap provides functionalities that enable an attacker to execute commands on the underlying operating system. This capability is particularly useful for gaining control over the target system and performing various actions, such as retrieving sensitive information or establishing persistence.
### Available Switches
SQLMap's help menu lists several switches under the "Operating System Access" section that facilitate operating system takeover. We will use the following ones:
- `--os-cmd`
- `--os-shell`
## Execution of System Commands
### The `--os-cmd` Switch
#### Description
The `--oscmd` switch allows the execution of commands on the target operating system.
#### Procedure
- Use the `--os-cmd` switch followed by the appropriate command.
- Example
```bash
sqlmap -u <target_URL> --os-cmd="<command>"
```
- Here is an the output of `ls` using `--os-cmd`:
	![[Pasted image 20240420033003.png]]
	![[Pasted image 20240420033034.png]]
	- note: the web server path needs to given, here it is `/opt/lampp/htdocs`
### The `--os-shell` Switch
#### Description
The `--os-shell` switch provides an interactive shell directly to the target operating system.
#### Procedure
1. Launch SQLMap with the `--os-shell` switch.
2. SQLMap attempts to upload its Stager and returns an interactive shell to the web server.
#### Example
```bash
sqlmap -u <target_URL> --os-shell
```
- Here is the command output:
	- after writing the command, see at the end of the terminal here that we are prompted to enter a command that will be executed at the server/victim.
	![[Pasted image 20240420033322.png]]
	- Output of a `touch john` using `--os-shell`:
		![[Pasted image 20240420033602.png]]
	- Here we see that a file `john` was created in the server machine:
		![[Pasted image 20240420033650.png]]
## Conclusion
By leveraging SQLMap's capabilities, attackers can effectively take over the target operating system, execute system commands, and establish persistent access.
# References
\[1] https://sourceforge.net/projects/xampp/files/XAMPP%20Linux/
\[2] https://github.com/Audi-1/sqli-labs