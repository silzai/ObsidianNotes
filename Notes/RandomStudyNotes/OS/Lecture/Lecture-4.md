# Processes and System Calls
# process states transition:
- fork will create a process -> process comes in job queue -> scheduler assign it to -> ready queue (processes that are loaded into memory, process will become "running" but can also be swapped to the disk if no space is available) -> short???queue (this is where CPU executes the processes)
- every process has a block in memory called PCB (process control block), its like the identity of process, as it contains the information about the process, such as process number.
- process may be executed, or waiting for io, in this case we suspend the process and sends it back to ready queue and choose another process
	- will use context switching to do this
	- context switching time is the idle time while processes are switching
- if process doesn't finish processing within time limit, then again will send to ready queue and choose another process (called round robin schedule)
- difference between kernel mode and user mode, is that kernel mode has all privileges to access system resources
# fork()
- fork() returns an integer negative, 0 or positive
- 0 and positive means that fork() was successful, otherwise failed
- fork duplicates the code
- `wait(NULL)` 
	- block the parents execution until the child finishes its execution
# exec()
- will replace the current process's remaining code
	- execlp stands for "execute and leave process"
- syntax: `execlp(“location”,actual_program,"program_options”,NULL);`
- exec may fail when:
	- parameter list that is passed is wrong
	- not enough memory
# wait()
- already said what it is in fork() section above
- every time child wants to exit, it takes an exit system code, 0 means successful termination, any other value is error
	- when child executes exit it just stops executing, but is still not yet removed completely
	- when parent executes wait(null), then only child is removed
	- after childs termination, exit code value is stored in `waitpid`

- Cascading Termination:
	- ex: if shell terminal is terminated, all its running children will also be terminated
# ==what is all this????==

