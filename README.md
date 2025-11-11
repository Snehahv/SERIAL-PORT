
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
ORG 00H
 MOV TMOD, #20H
 MOV TH1, #0FDH
 MOV SCON, #50H
 SETB TR1
 MAIN_LOOP:
 MOV SBUF, #'B'
 WAIT_TI:
 JNB TI, WAIT_TI
 CLR TI
SJMP MAIN_LOOP
 END
```
### (ii) Serial Port to Transfer a Message

```
 #include<reg51.h>
 void main(void)
 {
 unsigned char msg[]="Haridharan";
 unsigned char i;
 TMOD=0X20;//TIMER 1,MODE 2
 TH1=0XFC;
 SCON=0X40;
 TR1=1;
 for (i=0; i<17;i++)
 {
 SBUF= msg[i];
 while(TI==0);
 TI=0;
 }
 while(1);
 }
```

### OUTPUT:
<img width="573" height="290" alt="image" src="https://github.com/user-attachments/assets/ffa121fc-9140-452a-be82-357a5ef55bb9" />

<img width="576" height="292" alt="image" src="https://github.com/user-attachments/assets/88f5a220-511b-4555-88cd-6fbcfa234f94" />


### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
