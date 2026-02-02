# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4300H
MOV B, A
LDA 4301H
ADD B
STA 4400H
JC STORECARRY
HLT
STORECARRY: MVI A, 01H
STA 4401H
HLT
```
### Verification

<img width="357" height="525" alt="image" src="https://github.com/user-attachments/assets/b6837bad-33ee-4bcf-982f-1b6c0f6b443e" />

### Output:

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/8c98e904-61d6-448b-b368-813d4904f34e" />

### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
CMP C
JC SWAP
SWAP:
MOV B, A
MOV A, C
SUB B
STA 4300H
HLT
```
### Verification
<img width="377" height="630" alt="image" src="https://github.com/user-attachments/assets/438a10db-397b-4bbc-96f9-2bb33376a18c" />

### Output:
<img width="1918" height="1027" alt="image" src="https://github.com/user-attachments/assets/e61a16d4-0e13-49a4-93ef-0bf7facf0c3e" />

### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```
### Verification

<img width="407" height="737" alt="image" src="https://github.com/user-attachments/assets/f4612b9a-1519-4160-974c-036edca9b7d3" />

### Output:

<img width="1918" height="968" alt="image" src="https://github.com/user-attachments/assets/55fd3bfc-32c7-4e6c-8b1e-f880b27d90c3" />

### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
MOV B, A
MVI D, 00H
MVI A, 00H

LOOP: MOV A, C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END: MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```
### Output:


<img width="1918" height="1023" alt="image" src="https://github.com/user-attachments/assets/746006a6-13b6-440f-9761-7df92b264dea" />

### Verification

<img width="413" height="543" alt="image" src="https://github.com/user-attachments/assets/160f598f-e545-42cf-9643-529112799d68" />

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

