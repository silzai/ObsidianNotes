# Inter-Process Communication
- processes cannot share variables, so to make them communicate, we need pipes and signals
- is a one-way communication to read and write a stream of bytes (data)

# Types of Data:
- There are 2 types
## 1) Strings:
- `write()`
- `read()`
## 2) Commands:
- Will use `dup` first, meaning `duplicate`/or redirect from standard output to the pipe
 - `dup()`
 - `dup2()`
 - `exec()/system()`

# Unnamed Pipes
- 
- ends of processes that are not being read or written must be closed
- ==differentiate bw dup and dup2== but they are used to 
- problems with unnamed pipes (our 1st implementation)
	- there is limit on size of pipe (512 bytes) so 
	- once processes are terminated, the pipe cannot be referenced again 
# Named Pipes
- so a named pipe:
	- does not have a limit to its size
	- creates a file, and that file is used for the interprocess communication
	- is called FIFO (as is uses this style )
- to create it:
	- will use `mkfifo(fileName, permissions)`
	- give permission to the file to be read and written using the second argument, can use `0644` as argument for file to be read and write, for ex:
```c
mkfifo("myfifo", 0644) // creating named pipe
```

# Signals
- created by kernel or another process, can send software interrupt as a process
- there are total 64 signals in \*nix, 32 are standard signals, while there are other 32 signals left for the user to define
- a process can send an interrupt to another process
- Three ways to act with a signal, if a process send one:
	- the other process can accept the default action
	- the second, the process can ignore it, and continue its own execution
	- the third, handle the signal
```bash
kill -l # will show the list of signals we have
```
## examples:
- so `SIGPIPE` is sent to process to tell if pipe has failed
- and `SIGCHILD` is sent to parent to request for termination
## There are 2 signals that cannot be ignored:
- `SIGSTOP` and `SIGKILL` cannot be handled or ignored by processes, only default action will be taken
## To send a signal in the command line
- to send a signal, will use `kill` command
```bash
kill signal-to-be-sent pid
```

- example:
```bash
kill -SIGTERM 1234 # to SIGTERM used to terminate a process
```
## Signal Sources
- signals can be predictable (synchronized) or unpredictable (unsychronized)
- 
- 