# What is Pysical Memory memory

![image](https://github.com/user-attachments/assets/0b4f7ff2-2606-4440-80ad-5db7441efe92)

![image](https://github.com/user-attachments/assets/48537dfa-7faa-49db-b376-f66e6003be8b)

# What is virtual memory

Virtual memory is a mapping between an address space to an underlying physical device (or None). Where an address space is a collection of numbers that represent where each bit of the program will be stored.

If the virtual memory technique we have,

1. Address space an mapping in Virtual Space
1. Address space an mapping on devices (RAM)

The MMU (Memory management module) negotiates the two. The virtual memory can be mapped to,

1. RAM
1. SWAP
1. Device (GPIO... etc) (Change in bit in one, will cause a change in bit in the other)

Advantages
1.Ram can be mapped to multiple process and gives concept of shared memory.
1. Memory Regions can have access to permissions. ( read write execute)

![image](https://github.com/user-attachments/assets/28b7aa3e-8390-49f2-88e9-d7599449a982)

![image](https://github.com/user-attachments/assets/c1ca53a1-af23-4b8e-8ab7-1fab6a496400)


## The Virtual Memory translation

![image](https://github.com/user-attachments/assets/1696b1e4-f82b-4df3-a868-dcde9eb729f7)

![image](https://github.com/user-attachments/assets/5b93c13f-97a7-40d5-8b87-908acdd4ddf8)

![image](https://github.com/user-attachments/assets/8a33bb12-61a6-422d-9fea-57be6ce8cf09)

Assume we have only RAM, our mapping will be,

```mermaid
flowchart LR;
    subgraph virt["Virtual memory address list"]
        vbits["[0][1][2][3]..."]
    end
    subgraph RAM["Random Access Memory"]
        pbits["[0][1][2][3]..."]
    end
    subgraph mmu["Memory management module"]
        0-->22
        33-->56
    end
    virt<-->mmu
    mmu<-->RAM
```

The virtual memory is the range of addresses to be mapped. The mapping is done by hardware, called the MMU. (Some processors don't have these, but can still run linux)

When a program runs.

1. Is allocated a range in the virtual memory. Where it would have its bits.
1. Once a memory address is requested, its assigned a location in the physical memory.
1. When an app wants to store a bit, the kernel/MMU translates the location and stores the bit.

The virtual memory range is much larger then the actual memory (physical)

## SWAP

SWAP is a way to store some of the RAM memory on disk. That is once the kernel notices that memory availability is low, it will download some of the address locations in the virtual memory to disk (Algo, LRU) and keep a map of that. Then free that physical memory for use. If a program needs to run with that memory, then a page fault error occurs in the MMU, which traps execution until the kernel loads that memory from disk.


# Kernel Virtual Memory

![image](https://github.com/user-attachments/assets/1c0b0afa-5801-4762-8c14-4a1edc8b5e9e)

![image](https://github.com/user-attachments/assets/420b0766-9230-4b4a-8c31-8ea58bb1218d)

- On 64 bit you don't have to worry as 2 to power 64 is way greter memory that we perceive today

# Virtual Addresses
 
![image](https://github.com/user-attachments/assets/04e64d6e-72fa-4603-8719-052d09a8c5f4)

![image](https://github.com/user-attachments/assets/29e8426d-4ef7-49ba-a4fd-1a9f178c394a)


 ![image](https://github.com/user-attachments/assets/f6f9eb31-b492-49cb-b14c-1df28ebf0c21)

 ![image](https://github.com/user-attachments/assets/98fe0f50-97f0-4173-8bab-a95f5192d5e8)

 ![image](https://github.com/user-attachments/assets/8f9380c2-c8ef-40e1-937e-2c41d630c2ed)

 ![image](https://github.com/user-attachments/assets/c3a81061-79a4-4aa2-ae46-065c76e2b717)

![image](https://github.com/user-attachments/assets/5327fde7-e885-490d-8d86-a3043fc41d92)

 ![image](https://github.com/user-attachments/assets/dcb79a2d-c05e-4d8a-857b-2c847f868d8a)

![image](https://github.com/user-attachments/assets/187f89f5-302d-46e2-8c5e-dd03566f8e17)

![image](https://github.com/user-attachments/assets/2b3f3b14-0ba2-4b67-a71f-2daa26ea792d)

On 64 bit system, all memory is low memmory.

![image](https://github.com/user-attachments/assets/b0430ae7-f905-49de-95bf-402c15d1c523)

![image](https://github.com/user-attachments/assets/90fda82d-b4f1-4250-a2f8-83221dd27bf8)

![image](https://github.com/user-attachments/assets/d8fdebb4-1834-41c1-98aa-1c1d916c8f7c)

![image](https://github.com/user-attachments/assets/48c6d861-8aa5-4a01-b782-ee2893376d7b)


# User Virtual Memory

- It is non-continous and  page faults ; swap occurs and it needs to be shared across many processes.
- ![image](https://github.com/user-attachments/assets/015f3742-fb60-44a3-88ec-aab024584619)
- ![image](https://github.com/user-attachments/assets/0f9c1382-c65c-411c-af3c-43706ca608cc)

- ![image](https://github.com/user-attachments/assets/cd20677f-ba5c-41ce-b6f0-15816d815c20)

# MMU

![image](https://github.com/user-attachments/assets/a920ada7-71f2-4f8f-af1d-ef894e4205ad)

4k is common size for the page.
  
![image](https://github.com/user-attachments/assets/9f5a7784-4ac9-4047-9210-dc8b8270296f)

![image](https://github.com/user-attachments/assets/27b9a921-ed8f-43fd-95b2-d9293027aff4)

# Page Faults

![image](https://github.com/user-attachments/assets/c984f746-22e2-4341-bb29-fbdb3f4d1366)

![image](https://github.com/user-attachments/assets/8c79384d-11ea-415f-a803-fc1a28b8997f)

![image](https://github.com/user-attachments/assets/0cab2d3c-b84a-4855-b6ce-3636af45b990)

![image](https://github.com/user-attachments/assets/59c0fbe2-5460-417d-8d89-17aa57d2354b)

# Shared MEmory


#Lazy allocation
![image](https://github.com/user-attachments/assets/defe224b-a9c9-4629-976c-a0317bd52c31)

![image](https://github.com/user-attachments/assets/e602309f-9957-48b5-b221-4b7f9f10877c)

![image](https://github.com/user-attachments/assets/83a1a3f4-7508-4e29-99f5-11ad51732368)




