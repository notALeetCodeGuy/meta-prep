- Interrupt is generated using electronic signals and directed into input pins of the interrupt controller. The signal is sent to the processor.

![image](https://github.com/user-attachments/assets/3374853e-b8a1-463f-80c8-0a3179147a5a)

- Interrupt values are IRQ lines; Interrupt request lines.

- cat /proc/interrupts/
   - rtc0 (real time clock)
   - nvm - disk
   - pcie- grpahic
   - wifi interrupt
- IRQ zero is timer interrupt. and IRQ one is keyboard interrupt.
- Dynamic number will be alloted to other devices;
- Specific interrupt and specific.

- Code exceptions and traps are synchronous interrupt and hardware issues async interrupts.
- Interrupt handler are functions and are often called ISR ( interrupt servie routine)
- Interrupt is same like other functions only they run in Interrupt context; this context is atomic context because they are unable to block. 
- Process context  - kernel handles system calls
- Its important to run handler as fast as you can;; so that you can resume the exeution of interrupted code as soon as possible.

Top Halves and Bottom halves
- LEAST hardware can do is ack; that gives notion of concept of Top Halves and Bottom Halves.
- Take the data in Top Halves and pass it on to bottom halve.
- ![image](https://github.com/user-attachments/assets/1b2c2777-f40b-4287-8cf9-2997c1dc5969)
- Top in interrupt context and bottom half in normal context.
- Network Interrupt working:
   ![image](https://github.com/user-attachments/assets/589c2c00-7289-47b8-9b8f-a11146e25f7e)


  Regiswtering an interrupt handler:
  - Code for interrupt handler comes from the driver
![image](https://github.com/user-attachments/assets/aec4f00e-116f-4e08-b176-aa71874a2cc7)

COnfusing:
request_irq is not atomic.
![image](https://github.com/user-attachments/assets/ace9317e-3788-4bf1-9643-7ef5f738b0f1)





An example:  
![image](https://github.com/user-attachments/assets/aebb2e2c-ec24-4813-9e0a-b97236f9950e)
RTC : real time clock interrupt
Whenever a rtc driver loads; rtc_init is invoked?
Two values are returned from interrupt handler ; either IRQ_HANDLED or IRQ_NONE
There are locks inside the handler; so that another processsor does not pick up on that.
Process context can sleep or invoke the scheduler.

-----------------

Interrupt context is not associated with a process context.Without process context how can interrupt context can sleep?
If a function called from interrupt handler sleeps ; then it can't be called from interrupt handler; as there is no way to wake up without process context
Interrupt can interrup antoher interrup function on another line; but not on the same line as they are disabled.
_ Interrupt don't get their own stack; they share 2 pages or 8kb with the process which interrupted it.

<img width="760" alt="image" src="https://github.com/user-attachments/assets/26ed0260-c9f1-4ca6-828a-3cde3b229178" />

![image](https://github.com/user-attachments/assets/87e14aad-6f9e-4ab1-8705-f8a06066d9df)

- Disabling interrupts disables kernel preemtion.
-
- ![image](https://github.com/user-attachments/assets/3c87a794-ec06-480f-ae1a-528d5053cbce)

![image](https://github.com/user-attachments/assets/cdb82754-3b4a-4698-9f84-7a9a94644a35)
