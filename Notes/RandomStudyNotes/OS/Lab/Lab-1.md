ubuntu 
- username: basil
- password: 123

# Navigating the OS
## To see the location of where you are:
```bash
pwd
```
- pwd: print working directory
## To go back in the directory hierarchy
```bash
cd ..
```
- and we can add slashes to the dots to go back multiple directories
```bash
cd ../..
```
- This will go back 2 directories
# To run a program
```bash
./<the program name>
```
- Will add `./` to run the program, the `.` represents the current directory, but its needed to run a program from a relative path
- 
# Help
## To see info about a command
```bash
man <the command>
```
- man: manual
- the command: the command you want to see the features about
OR 
```bash
<the command> --help
```
OR 
```bash
info <the command>
```

- can search for regex in help like so:
```bash
man -k <regex>
```

# Sudo
- to switch to super user:
```bash
sudo su
# then enter password
```
- We can create new users directly while in sudo, this is in sudo because we are modifying the OS file system:
```bash
useradd -m user1
```
- To see privileges or properties of all files:
```bash
ls -l
```
- To view short file content:
```bash
cat <filename>
```
- to redirect input from std input to any file (to write to a file):
```bash
cat > <fileToWriteTo>
# then to save, do ctrl + d
```
- to append to the file, as previous text will be overridden:
```bash
cat >> <fileToWriteTo>
```
# Regex
- Square brackets represent one character

# Deleting Files/Folders
- To remove files:
```bash
rm <fileName>
```
- To remove directory containing files:
```bash
rm -r <directoryName>
```
# Copying/Moving/Renaming Files
- To copy files from one dir to another dir:
```bash
cp -r dirOne/* dirTwo/
```
- the `-r` is used because `dirOne/` may contain folders also, so we also want to copy those folders also.

- To rename a dir to another dir:
```bash
mv dirOne/ dirTwo
```
- to move a dir to another dir:
```bash
mv dirOne dirTwo/
```
# grep
- to search for a string in a file
- 