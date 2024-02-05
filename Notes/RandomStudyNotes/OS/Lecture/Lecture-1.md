# Content:
- History
- Linux Operating System

- OS manages the hardware, resources are managed by OS
- Kernel: There are many modules in an OS, to manage these modules, Kernel is used, so it is the core of the OS

- Modern operating system: has multi-users and multi-tasking (timeshared systems)
# History/Types of Operating Systems:
- Uni-Processing: 1 process at a time
- Batch Systems: cards with similar jobs are grouped for processing but still no interaction with users.
- Multi-programmed systems:
- Parallel Systems has 2 types:
	- symmetric multiprocessing (smp):
	- asymmetric multiprocessing (amp):
		- processors cannot communicate with each other, there is master slave communication, so time is saved
		- not used in normal end devices
		- these CPUs have higher capabilities than SMP CPUs
		- because there is high intensive CPU capabilities, used for high performance computing (HPC)
- Real Time Systems: 
	- execution of processes are sensitive to the time; delay is an important aspect; processes must finish within a deadline
	- such as medical imaging, surgery, autonoumous automotives etc.
	- doesn't have secondary storage device, because takes time
	- is directly loaded from ROM, or at that time
- Distributed Systems:
	- CPUs over a network

# OS Structures:
## Simple Structure:
- very limited functionality and hardware
- kernel space is very small
- ex: MS-DOS
>[!warning]
>not secure because user/application program has direct access to hardware

>[!warning] 
>if program fails, entire OS will crash, then will have to restart, its a single point of failure
- resident system program: similar to the kernel
## Layered Approach:
- can separate services by OS to $m$ layers
- every layer can communicate with adjacent layer above and below only
- is modifiable, has modularity
- example: OS/2 
- disadvantages:
	- performance is slow (intercommunication between layers is time consuming)
	- don't know the appropriate number of layers to apply (layers may be too much, or too less)
## Microkernel:
- only the essential components are kept in the kernel, ex: memory management
- all other components are on user side, ex: file management
- examples: Minix, Symbian
- is extensible: can add services to the user level, is portable
- increased overhead from mapping from user level to kernel level is done, so performance is slow
## Monolithic Kernel:
- opposite of microkernel, as we just move everything from in user level to the kernel 
- increases performance
- examples: openBSD, Ms Windows
- not extendable, not modifiable, is single point of failure
## Modular Kernel
 - one kernel program that manages all services of OS
 - example: UNIX
# SYSGEN
- ==?????==
# Virtual Machines
- exact copy of an underlying hardware
- each runs on separate address space, but actually runs on same hardware
# SHELL
- Two implementation of Command-Interpreter:
	- implementation A: all commands (functions) are loaded and the  
	- implementation B: one main function, and all commands are called one by one from the /bin directory
- (for windows, the same is batch scripting with .bat extension, which is same as shell script)
## Commands
- to list the the permissions that a user has:
	- `ls -l test.sh`
- we can assign permissions by octal numbers, because the permissions such as `rwx` is 7 (u), `rw-` is 6 (g), `r--` is 4 (o) 
- so to assign all permissions: `chmod 777 test.sh` or `chmod a+rwx` instead of `chmod ugo+rwx`
## Scripting
- `$` with the variable is used to get the actual value in the variable
- any arithmetic should be with `let`
- to store keywords in string, will need to use back quotes \`\` or `$(pwd)` in the string
