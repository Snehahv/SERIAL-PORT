
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

![WhatsApp Image 2025-11-13 at 08 22 42_1e84ef94](https://github.com/user-attachments/assets/8bb5067b-9453-483e-8091-0c8e9d595644)

![WhatsApp Image 2025-11-13 at 08 22 43_6ac001c2](https://github.com/user-attachments/assets/92715e2e-599e-4a04-b39c-19a8b87388d8)


### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
