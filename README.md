1.Write an assembly language program in 8051 to generate a 2 ms delay using Timer 0 in Mode 1 and toggle an LED connected to Port 2.0.

AIM

To write an assembly language program in 8051 to generate a 2 ms delay using Timer 0 in Mode 1 and toggle an LED connected to Port 2.0.

APPARATUS REQUIRED

Personal  computer

ALGORITHM:

Start the program.

Initialize Port 2 as output by loading 00H into P2.

Set Timer 0 in Mode 1 (16-bit timer mode) by loading TMOD with 01H.

Load the timer registers:

TH0 = F8H

TL0 = 30H
(This gives approximately 2 ms delay for a 12 MHz crystal.)

Start Timer 0 by setting the TR0 bit.

Wait until the Timer Overflow Flag (TF0) becomes 1 (indicating the delay period is complete).

Stop Timer 0 by clearing the TR0 bit.

Clear the overflow flag TF0 to prepare for the next delay cycle.

Toggle the LED connected to Port 2.0 using CPL P2.0.

Repeat steps 4–9 continuously to keep toggling the LED.

End the program.

PROGRAM:

     ORG 0000H
    START:
    MOV P2, #00H        
    MOV TMOD, #01H      
    MAIN:
    MOV TH0, #0F8H      
    MOV TL0, #30H       
    SETB TR0            
    WAIT:
    JNB TF0, WAIT       
    CLR TR0             
    CLR TF0             
    CPL P2.0            
    SJMP MAIN           
    END
OUTPUT:
<img width="1311" height="703" alt="image" src="https://github.com/user-attachments/assets/92e962ec-cebd-426a-9609-a161ff5c9292" />

<img width="1600" height="987" alt="image" src="https://github.com/user-attachments/assets/2cc87212-b1c7-4226-b321-fd669c0b9a83" />

RESULT:
Thus the assembly language program in 8051 to generate a 2 ms delay using Timer 0 in Mode 1 and toggle an LED connected to Port 2.0 was executed successfully using keil and proteus




