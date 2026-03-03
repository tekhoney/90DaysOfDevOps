Day 02 – Linux Architecture, Processes, and systemd



The core components of Linux are as below

Kernel
Kernel is know as core of linux or heart of linux 
Shell
Shell is another component of linux, which is also know as mediator between end user and Kernel. we execute commands using shell. 
Apllication(End user)
user interact with OS using applications, This is mainly a ASK model A=application, S=SHELL, K=kernel.


How processes are created and managed

Everything in linux is a PROCESS, means whatever we do (from starting system to shutting it down) linux create process with their PID of every event.
For example:
- when we turn on the system the very first process is INIT/systemd with PID 1,
-then we open the browser it will start another process with differrent PID and same with other applications.

What systemd does and why it matters

Systemd is a default service manager in linux, when we boot the system BIOS loads the kernel and kernal loads the SYSTEMD and systemd starts all the services in the ubuntu 
that is why we call it the first process in the system. 

Process:- when we perform any task we have to start and end the task to complete it, so the steps we have followed to complete the task are called process. these processes can be multiple types 

New → Ready → Running → Waiting → Running → Terminated

Explain process states (running, sleeping, zombie, etc.)

Runnung process:-
the process which is not completed and consuming the hardware resources like CPU, Ram, HDD are called running process. 

sleeping process:
when the process is waiting for any required component, it could be resources or user's instruction is called sleeping process. 

Zombie processes: 
zombie process is child a process who's parent process has been executed or killed. 

List 5 commands you would use daily

cd - change directory

Pwd - present working directory 

grep - to find something 

chmod - to set the permissions 

ls -lrth - to list in the human readable form

ps - to check process 
top - to check the resource consumption by any process. 

