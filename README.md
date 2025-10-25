# 200 µs delay using Timer 0 in Mode 1 and Toggle Port 0.1

## AIM:

To write and execute an Assembly language program to generate a $200 \mu s$ delay using Timer 0 in Mode 1 and toggle Port 0.1 using 8051 Keil.

---
## APPARATUS REQUIRED:

- Personal computer with Keil software

---

## ALGORITHM:

1. **Start**
2. **Initialize Timer:** Set TMOD to 01H (Timer 0, Mode 1: 16-bit timer)
3. **Initialize Port:** Set the initial state of P0.1 (e.g., $\text{SETB P0.1}$).
4. **Load Timer:** Calculate and load the 16-bit count for a $200 \mu s$ delay into $\text{TH0}$ and $\text{TL0}$ (e.g., $\text{FF38H}$)
5. **Start Timer:** Set the TR0 bit to start Timer 0.
6. **Wait for Overflow:** Monitor the TF0 (Timer 0 Overflow Flag). Wait until $\text{TF0}$ is set ($\text{TF0}=1$).
7. **Stop Timer:** Clear the $\text{TR0}$ bit to stop Timer 0.
8. **Clear Flag:** Clear the $\text{TF0}$ bit.
9. **Toggle Port:** Complement the state of P0.1 ($\text{CPL P0.1}$).
10. **Loop:** Jump back to step 4 to repeat the process.
11. **End**
    
---

## FLOWCHART:

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/389ae382-4a84-4ef1-90da-874967d124d6" />

---

## PROGRAM:

ORG 0000H

MAIN:   MOV TMOD, #01H        
        SETB P0.1             

TOGGLE: CPL P0.1              
        ACALL DELAY_200US     
        SJMP TOGGLE          

DELAY_200US:
        MOV TH0, #0FFH        
        MOV TL0, #038H        
        SETB TR0              

WAIT:   JNB TF0, WAIT         
        CLR TR0               
        CLR TF0
        RET
END

---

## OUTPUT:

<img width="1579" height="560" alt="image" src="https://github.com/user-attachments/assets/ba8ae79f-6f59-4b16-9161-70acc5716733" />
<img width="625" height="404" alt="image" src="https://github.com/user-attachments/assets/847f3a22-432c-471b-a1cb-397a49eecb8a" />


## RESULT:

Thus, an Assembly language program to generate a $200 \mu s$ delay using Timer 0 in Mode 1 and toggle Port 0.1 was written and simulated/executed successfully using 8051 Keil.

---
