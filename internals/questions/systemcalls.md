- device files and proc accessed via system calls
- kernal space - exceptions, traps and systems calls entry point
- - tell kernel want to executte sys call; signal to switch to kernel mode; so system operations happen in kernel mode but still in process context ( current pointer 
    still referencing the process)
- signal is interrupt in linux systems
- interrupt is signal and signal handler is sys call handler.
- interrupt is trigged via 128 instrcutions in x86 and switch to kernel mode.
- sys call number is sent to kernel via eax rregister. user space puts in the register as they don't share same space.
- checks validity against NR_syscalls ; and syserrno if its not valid.
- arguments and return value are passed via register. to user space and user space writes to std out.
- pointer to all the values are store in user space
- results are stored in eax register

Implementing sys call:

- VFerifying the poninter provided to sys call should be validaed throughly, around permissions and validity of that pointer
       - Dont read kernel space
       - Don't read other process space


Q: What is buffer and how it is different address soace?

<img width="552" alt="image" src="https://github.com/user-attachments/assets/0d6eb9f7-ceb1-4529-88db-a7335ff2c366" />


<img width="1066" alt="image" src="https://github.com/user-attachments/assets/ee0ba674-a07f-4d3b-9a1b-634f6578cbcb" />


Sys calls/kernel is premitible and syscall should be reentrant - means should know for which process it is running the sys call.
