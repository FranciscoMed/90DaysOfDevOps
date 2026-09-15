# Linux Day

## Goals
1. The core components of Linux (kernel, user space, init/systemd)
2. How processes are created and managed
3. What systemd does and why it matters
4. Explain process states (running, sleeping, zombie, etc.)
5. List 5 commands you would use daily

## Kernel
The Kernel is the link between hardware and software it manages CPU, Memory, Processes, Storage.
As a DevOps engineer we may need to check the kernel version, modules and troubleshoot the kernel messages. 
A part of troubleshooting is to know how containers rely on the host's kernel. Container runtimes take advantage of process namespaces to isolate their own resources.

## User Spaces
The User space is where Users and applications live, it seperates the OS from it's applications so if one application crashes it does not bring the whole system down.
It also limits the powers/permissions of applications. To each application/user their own set of permissions. Improving Stability, Security and resource allocation.

## SystemD
It's the first process to start, it initializes all application and services in the User Space, it monitors the services and can handles the dependencies between them.
It matters because it's the process that starts/stops all other applications/services, it is an integral part of troubleshooting applications/services.

## Process States
- Running: When a process has CPU time and is actively using the CPU or is ready to use it
- Sleeping: When a process is waiting for some action (user input, networking, reading a file)
- Uninterruptable Sleep: When a process it waiting on hardware I/O
- Stopped: The process has been paused, by a _ctrl+z_ or a debugging tool (_sleep 300_)
- Zombie: The process has finished it's execution but it still has an entry in the process table, meaning it's parent process has not colletected it's exit status

Every process has a parent, tracing back to systemd (PID 1), which sits at the root of the process tree and adopts orphaned processes when necessary.

## 5 Command Bible
   _ps_ -> Check Process table
   _top_ -> Check Resource usage and process activity in real time
   _systemctl_-> Used to interact with system services
   _journalctl_ -> Used to check system services logs
   _grep_ -> Search trough files (Outputs and logs)
   _cat_ -> open a file
   _tail_ -> displays last lines of the file
   _less_ -> open a chunk of the file
