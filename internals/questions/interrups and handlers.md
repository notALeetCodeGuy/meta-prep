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


