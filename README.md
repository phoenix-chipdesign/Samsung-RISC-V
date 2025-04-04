# Samsung-RISC-V
NAME: Rohan V Poorma  
College: KLE Institute of Technology  
EmailID:rohanpoorma7@gmail.com   
Github:https://github.com/phoenix-chipdesign   

<details>
<summary><b>Task 1:</b>Task is to install all the essential tools required for this samsung-RISCV  Workshop such as Ubuntu on VMBox & refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler</summary><br>

### Install Ubuntu 20.04 LTS on Oracle Virtual Machine Box

Firstly, I have downloaded the virtual box from the links provided to us and
loaded a linux version with image dock file sent  
![Ubuntu and VMBox Installation](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/virtual_machine_installed.png)

### C Language based LAB
I have successfully run the virtual machine and compiled the tasks.

Initial task is:-

### write a program to compile the sum of first 5 natural numbers in c:

we have written the code sum of 1st 5 numbers in leafpad as shown below.

```
gcc sum_1ton.c

./a.out
```

this code will be run in terminal to get output as 15 for 1st 5 numbers as shown below :


![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/cat%20Command.png)

### RISCV based LAB

1. Using the cat command, the entire C code will be displayed on the terminal.
   
![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/RISCV_C_CODE_O1.png)

2. A program is run to obtain risc-v version of the code previously written in c:

  	 ```
	riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
	```

![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/RISCV_CODE_Ofast.png)


3. As the whole version of above code looks lengthier we have used below code to make it shorter
	
 	```
	riscv64 -unknown-elf-objdump -d sum1ton.o | less
	```
 
& we have obtained the required main part to compare the execution in assembly language as shown below :

	
 
![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/Objdump%20using%20-Ofast%20format.png)

4. Open the same terminal and run the given command:
 
 	```
	riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
	``` 


![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/Objdump%20using%20-O1%20format.png)

5. As the whole version of above code looks lengthier as earlier we have used below code to make it shorter
	
 	```
	riscv64 -unknown-elf-objdump -d sum1ton.o | less
	```
 
& we have obtained the required main part to compare the execution in assembly language as shown below :

![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%201/C%20Code%20compiled%20on%20gcc%20Compiler.png)

### End of 1st task
</details>

------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>Task 2:</b>SPIKE Simulation and Debugging the C code with Interactive Debugging Mode using Spike.</summary><br>
	

### SPIKE in RISCV?
Spike is a free, open-source C++ simulator for the RISC-V ISA that models a RISC-V core and cache system. It can be used to run programs and a Linux kernel, and can be a starting point for running software on a RISC-V target.

### Testing the SPIKE Simulator for sum1ton.c
**spike_O1_objdump**

**-O1_format**

![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/Spike%20O1%20objdump%20for%20sum1ton.png)

* Initially, the register a0 held the value 0x21000 (hexadecimal).
* After execution, the value of a0 changed to 0x21180 (hexadecimal).
* This change occurred because 384 was added in decimal, resulting in the updated value. 

**spike_Ofast_objdump**
**_Ofast_objdump**


![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/Spike%20Ofast%20objdump%20for%20sum1ton.png)

* Initially, the register sp held the value 0x3FFFFFFB50 (hexadecimal).
* After execution, the value of sp changed to 0x3FFFFFFB40 (hexadecimal).
* This change occurred because -16 was subtracted in decimal, resulting in the updated value.

### Factorial of n number (C program):

**Here i have used n value as 9**

![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/Factorialofn.png)

**objdump_O1_format**


![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/O1%20objdump%20for%20factorialofn.png)

**objdump_Ofast_format**



![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/Ofast%20Objdump%20for%20factorialofn.png)


### Testing the SPIKE Simulator for factorialofn.c
**spike_O1_objdump**

**-O1_format** 

![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/Spike%20O1%20objdump%20for%20factorialofn.png)

* Initially, the register a0 held the value 0x2B000 (hexadecimal).
* After execution, the value of a0 changed to 0x2AC90 (hexadecimal).
* This change occurred because -880 was subtracted in decimal, resulting in the updated value.

**Spike_Ofast_objdump**

**-Ofast_format** 



![image](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%202/Spike%20Ofast%20objdump%20for%20factorialofn.png)

* Initially, the register sp held the value 0x3FFFFFFB50 (hexadecimal).
* After execution, the value of sp changed to 0x3FFFFFF20 (hexadecimal).
* This change occurred because -48 was subtracted in decimal, resulting in the updated value.



### End of 2nd task
</details>

------------------------------------------------------------------------------------------------------------------


<details>
<summary><b>Task 3:</b> Task is to identify various instruction type of all the given instructions with its exact 32 bits instruction code. </summary>

### INSTRUCTIONS FORMAT IN RISC-V  
 
There are 6 instruction formats in RISC-V:  
1. R-format  
2. I-format  
3. S-format  
4. B-format  
5. U-format  
6. J-format

### 1. R-type Instruction  
* In RV32, each instruction is of size 32 bits.
* In R-type instruction, R stands for register
* This instruction type is used to execute various arithmetic and logical operations.
* The entire 32 bits instruction is divided into 6 fields as shown below.
![R-type](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%203/R_type_instruction.png)

### 2. I-type Instruction  
* In RV32, each instruction is of size 32 bits.
* In I-type instruction, I stand for immediate which means that operations use Registers and Immediate value
* This instruction type is used in immediate and load operations.
*  The entire 32 bits instruction is divided into 5 fields as shown below.

![I-type](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%203/I_type_instruction.png)

**Example: ADDI rd, rs1, imm**


### 3. S-type Instruction  

* In RV32, each instruction is of size 32 bits.
*  In S-type instruction, S stand for store which means it is store type instruction that helps to store the value of register into the memory.
*  Mainly, this instruction type is used for store operations.
*  The entire 32 bits instruction is divided into 6 fields as shown below.  
  
![S_type_instruction](https://github.com/user-attachments/assets/7af476e1-94ee-466c-935b-d9ee5000b1ec)


**Example: SW rs2, imm(rs1)**


### 4. B-type Instruction  
* In RV32, each instruction is of size 32 bits.
* In B-type instruction, B stand for branching which means it is mainly used for branching based on certain conditions.
*  The entire 32 bits instruction is divided into 8 fields as shown below.  
  
![B-type](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%203/B_type_instruction.png)

**Example: BEQ rs1, rs2, imm**   
 
  
### 5. U-type Instruction  
* In RV32, each instruction is of size 32 bits.
*  In U-type instruction, U stand for Upper Immediate instructions which means it is simply used to transfer the immediate data into the destination register.
*  The entire 32 bits instruction is divided into 3 fields as shown below.  
  
![u-type](https://github.com/phoenix-chipdesign/Samsung-RISC-V/blob/main/Task%203/U_type_instruction.png)

**Example: LUI rd, imm**   

  
### 6. J-type Instruction  
* In RV32, each instruction is of size 32 bits.
* In J-type instruction, J stand for jump, which means that this instruction format is used to implement jump type instruction.
*  The entire 32 bits instruction is divided into 6 fields as shown below.  
  
![J_type_instruction](https://github.com/user-attachments/assets/1f9d091d-a1f9-4ac7-9ff9-8e6071fdbd1a)


**Example: JAL rd, imm**

### There are 15 unique instructions from RISCV objdump application as follows:
------------------------
### 1. JAL ra 10408 <printf>

![JAL_J_type](https://github.com/user-attachments/assets/e6aee0d7-2236-4d33-a7ef-9ddfece0cae9)

> * In this instruction JAL means Jump and Link,  
> * hence this instruction belongs to the J-type instruction set.

- **Immediate (20 bits)**: 0 1001100000 1 00001010 (split into imm[20] = 0 and imm[10:1] = 1001100000 imm[11] = 1 and imm[19:12] = 00001010)  
- **rd (ra = x1)**: 00001  
- **Opcode**: 1101111  

**32 bits instruction:**  
0 1001100000 1 00001010|00001|1101111  

---  

### 2. LD ra 8(sp)

![LD_I_type](https://github.com/user-attachments/assets/1c0d8506-db98-45da-b412-5e2f1180b59e)

> * In this instruction LD means load doubleword instruction,  
> * hence this instruction belongs to the I-type instruction set.

- **Immediate :** 000000001000 (split into imm[11:5] = 0000000 and imm[4:0] = 01000)  
- **rs1 = sp :** 00010  
- **rd = ra :** 00001  
- **funct3:** 011  
- **Opcode for LD:** 0000011  

**32-bit instruction:** 0000000|00001|00010|011|01000|0000011  

---  

### 3. BEQZ a5 101f0 <exit+0x2c>

![BEQZ_B_type](https://github.com/user-attachments/assets/8e3d4a6a-59fa-4afd-be84-5b38e3c0185b)

**The BEQZ pseudo-instruction means "branch if equal to zero" and is equivalent to:  
BEQ a5, x0, offset**  

> * In this instruction BEQZ means pseudo-instruction, short for "branch if equal to zero."  
> * Hence this instruction belongs to the B-type instruction set.

- **Immediate :** 1000000011100 (split into imm[12] = 1, imm[10:5] = 000000, imm[4:1] = 01110, imm[11] = 0)  
- **rs1 = a5 :** 01111  
- **rs2 = x0 :** 00000  
- **funct3:** 000  
- **Opcode for BEQ:** 1100011  

**32-bit instruction:** 1000000|00000|01111|000|01110|1100011  

---  

### 4. ADDI sp, sp, -16

![ADDI_I_type](https://github.com/user-attachments/assets/a26a328f-86e3-44bd-8197-b1d63b14179a)

> * In this instruction ADD means Addition, I means Immediate,  
> * hence this instruction belongs to the I-type instruction set.

- **Opcode for ADDI :** 0010011  
- **rd = sp :** 00010  
- **rs1 = sp :** 00010  
- **imm[11:0] = -16 :** 111111110000  
- **func3 :** 000  

**32 bits instruction:**  
111111110000|00010|000|00010|0010011  

---  

### 5. LUI a0 0x21

![LUI_U_type](https://github.com/user-attachments/assets/9dcdd9ba-600f-489a-90cb-2bf6a806bbd8)

> * In this instruction LUI means Load Upper Immediate,  
> * hence this instruction belongs to the U-type instruction set.

- **Immediate = 0x21 :** 0000000000000_00100001  
- **rd = a0:** 01010  
- **Opcode:** 0110111  

**32 bits instruction:**  
0000000000000|00100001|01010|0110111  

---  

### 6. SRAI s1 a5 0x3

![SRAI_I_type](https://github.com/user-attachments/assets/e1236784-f266-45a2-a05e-67706beeb944)

> * In this instruction SRAI means Shift Right Arithmetic Immediate.  
> * Hence this instruction belongs to the I-type instruction set.

- **Immediate :** 000000000011 (split into imm[11:0] = 000000000011)  
- **rs1 = a5 :** 01111  
- **rd = s1 :** 01001  
- **funct3:** 101  
- **Opcode for SRAI :** 0010011  

**32-bit instruction:** 000000000011|01111|101|01001|0010011  

---  

### 7. MV a1 a0

![MV_R_type](https://github.com/user-attachments/assets/0b0164b6-a416-48d5-8602-74cea98d939f)

**The MV (Move) instruction is a pseudo-instruction in RISC-V, which is equivalent to:  
ADD a1, a0, x0**  

> * In this instruction MV means pseudo-instruction,  
> * hence this instruction belongs to the R-type instruction set.

- **rs1 = a0 :** 01010  
- **rs2 = x0 :** 00000  
- **rd = a1 :** 01011  
- **funct3:** 000  
- **Opcode for ADD :** 0110011  

**32-bit instruction:** 0000000|01010|00000|000|01011|0110011  

---  

### 8. SD ra 8(sp)

![SD_S_type](https://github.com/user-attachments/assets/eab1ca7b-f6ef-48a0-8ea5-beb055acd129)

> * In this instruction SD means store doubleword instruction,  
> * hence this instruction belongs to the S-type instruction set.

- **Immediate :** 000000001000 (split into imm[11:5] = 0000000 and imm[4:0] = 01000)  
- **rs1 = sp :** 00010  
- **rs2 = ra :** 00001  
- **funct3:** 011  
- **Opcode for SD :** 0100011  

**32-bit instruction:** 0000000|00001|00010|011|01000|0100011  

---

### 9. LBU a5, 1944(gp) # 231a0 <completed.5468>

![image](https://github.com/user-attachments/assets/8f009b1b-1992-45c9-a6ee-aab390d88532)

> * In this instruction LBU means Load Byte Unsigned,
> * hence this instruction belongs to I-type instruction set

- **Immediate :** 11110001000
- **rs1 = gp :** 00011
- **rd = a5 :** 01111
- **funct3:** 100
- **Opcode for LBU:** 0000011

**32-bit instruction:** 11110001000|00011|100|01111|0000011

--------------------
### 10. BENZ a5,10188 <do global dtors aux+0x4c>
    
![image](https://github.com/user-attachments/assets/31d8c899-4b38-4779-95d8-ed01a5ca0023)

**Assume that BENZ behaves similarly to a branch instruction, but with a custom format. We can treat BENZ like a branch if not zero instruction**

> * In this instruction BENZ means a specific operation (hypothetical or custom instruction), 
> * hence this instruction belongs to a custom instruction type.

- **Immediate :** 0000011010010 (split into imm[12] = 0, imm[10:5] = 000001, imm[4:1] = 1010, imm[11] = 0)
- **rs1 = a5 :** 01111
- **rs2 = x0 :** 00000
- **funct3:** 001
- **Opcode for custom BENZ:** 1100011

**32-bit instruction:** 0000001|00000|01111|001|1010|1100011

--------------------
### 11. AUIPC a5 0xffff0

![image](https://github.com/user-attachments/assets/dc1b9458-2bce-4ea9-89c1-610b5170cd78)

> * In this instruction AUIPC means Add Upper Immediate to PC Immediate,
> * hence this instruction belongs to U-type instruction set.

- **Immediate :** 11111111111100000000 (split into imm[31:12] = 111111111111 and imm[11:0] = 000000000000)
- **rd = a5 :** 01111
- **Opcode for AUIPC :** 0010111

**32-bit instruction:** 111111111111|01111|0010111

--------------------
### 12. SLLI t0, t0,0x1f

![image](https://github.com/user-attachments/assets/caf27b0e-ce37-48a5-b43f-d278bd3c3c11)

> * In this instruction, SLLI means Shift Left Logical Immediate,
> *hence this instruction belongs to the I-type instruction set.

- **Immediate :** 000000011111 (12-bit immediate value for 0x1f)
- **rs1 = t0 :** 00101
- **rd = to :** 00110
- **funct3:** 001
- **Opcode for SLLI :** 0010011

**32-bit instruction:** 000000011111|00101|001|00110|0010011

--------------------
### 13. J 101b0 <atexit> 

![image](https://github.com/user-attachments/assets/d837a001-3588-4ea7-9627-851fb5ff4cc3)

> * In this instruction J means Jump and Link,
> *  hence this instruction belongs to J-type instruction set.

- **Immediate :** 0000010000001101010 (split into imm[20] = 0, imm[10:1] = 0000000000, imm[11] = 0, imm[19:12] = 00000100)
- **rd = x0 :** 00000
- **Opcode for J-type (JAL):** 1101111

**32-bit instruction:** 0000000|0000000000|0|00000100|00000|1101111

--------------------
### 14. LW a0 0(sp)

![image](https://github.com/user-attachments/assets/8aa35f2b-bcd2-4619-a3dd-d22d0f706dff)

> * In this instruction, LW means Load Word,
> * hence this instruction belongs to I-type instruction set.

- **Immediate :** 000000000000
- **rs1 = sp :** 00010
- **rd = a0 :** 01010
- **funct3:** 010
- **Opcode for LW :** 0000011

**32-bit instruction:** 000000000000|00010|010|01010|0000011

--------------------
### 15. LI a0 0

![image](https://github.com/user-attachments/assets/732699d9-8bdf-48e5-bbce-ff775e79ea57)

**The LI pseudo-instruction means "Load Immediate" and is equivalent to an ADDI (Add Immediate) instruction** 

> * In this instruction LI means Load Immediate,
> * hence this instruction belongs to I-type instruction set

- **Immediate :** 000000000000 (12 bits)
- **rs1 = x0 :** 00000
- **rd = a0 :** 01010
- **funct3:** 000
- **Opcode for ADDI:** 0010011

**32-bit instruction:** 000000000000|00000|000|01010|0010011
### End of 3rd task
</details>

------------------------------------------------------------------------------------------------------------------


<details>
<summary><b>Task 4:</b> Use this RISC-V Core Verilog netlist and testbench for functional simulation experiment. </summary>

Reference GitHub repo is [![GitHub](https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/vinayrayapati/rv32i/blob/main/iiitb_rv32i.v)

## Starting with Functional Simulation
* First I installed the iverilog and gtkwave using following commands:
  ```
  sudo apt-get update
  ```
  ```
  sudo apt-get install iverilog gtkwave
  ```
* Cloning the github repository:
  - make a github repository
  - upload the two filies
  - 1. https://github.com/phoenix-chipdesign/phoenix/blob/main/iiitb_rv32i.v
    2. https://github.com/phoenix-chipdesign/phoenix/blob/main/iiitb_rv32i_tb.v
  -  run the below code in cmd 

  ```
   git clone https://github.com/phoenix-chipdesign/phoenix
   ```

* Chanding the working directory to `phoenix` using the following comand:
  ```
   cd phoenix
  ```

* To simulate and run the verilog code , entered the following commands in the terminal:
  ```
  iverilog -o phoenix iiitb_rv32i.v iiitb_rv32i_tb.v
  ```
  ```
  ./phoenix
  ```
* For seeing the output waveform I used the following command:
  ```
  gtkwave iiitb_rv32i.vcd
  ```

* The GTKWave will be opened and following window will be appeared  
  
![image](https://github.com/user-attachments/assets/8ebb8c40-d549-4bd2-9521-92a4200b617c)

### As shown in the figure below, all the instructions in the given verilog file is hard-coded, the designer has hard-coded each instructions based on their own pattern. Hence the 32-bits instruction that we generated in above task will not match with the given instruction.

![image](https://github.com/user-attachments/assets/512edc06-4524-43f7-833f-e3d087869a38)

#### Following are the differences between standard RISCV ISA and the Instruction Set given in the reference repository:  
  
|  **Operation**  |  **Standard RISCV ISA**  |  **Hardcoded ISA**  |  
|  :----:  |  :----:  |  :----:  |  
|  ADD R6, R2, R1  |  32'h00110333  |  32'h02208300  |  
|  SUB R7, R1, R2  |  32'h402083b3  |  32'h02209380  |  
|  AND R8, R1, R3  |  32'h0030f433  |  32'h0230a400  |  
|  OR R9, R2, R5  |  32'h005164b3  |  32'h02513480  |  
|  XOR R10, R1, R4  |  32'h0040c533  |  32'h0240c500  |  
|  SLT R1, R2, R4  |  32'h0045a0b3  |  32'h02415580  |  
|  ADDI R12, R4, 5  |  32'h004120b3  |  32'h00520600  |  
|  BEQ R0, R0, 15  |  32'h00000f63  |  32'h00f00002  |  
|  SW R3, R1, 2  |  32'h0030a123  |  32'h00209181  |  
|  LW R13, R1, 2  |  32'h0020a683  |  32'h00208681  |  
|  SRL R16, R14, R2  |  32'h0030a123  |  32'h00271803  |
|  SLL R15, R1, R2  |  32'h002097b3  |  32'h00208783  |  

### **Instruction 1: ADD**

![image](https://github.com/user-attachments/assets/f1b4a40d-b584-4fde-bb48-2132a76a858d)

**Overview:**
- The ADD instruction performs an arithmetic addition between two register values and stores the result in a specified destination register.

**Execution Details:**
1. The instruction `ADD R6, R1, R2` (0x02208300) is fetched from memory.
2. The values stored in registers R1 and R2 are identified as 1 and 2, respectively.
3. The Arithmetic Logic Unit (ALU) executes the addition: `1 + 2 = 3`.
4. The result (3) is written into register R6.

---

### **Instruction 2: SUB**

![Screenshot 2025-01-22 220359](https://github.com/user-attachments/assets/934478f0-3c8a-4698-ab99-9c9742883fb7)

**Overview:**
- The SUB instruction performs a subtraction operation between two register values and stores the result in a specified destination register.

**Execution Details:**
1. The instruction `SUB R7, R1, R2` (0x02208380) is fetched.
2. The values in registers R1 and R2 are 1 and 2, respectively.
3. The ALU processes the subtraction: `1 - 2 = -1`.
4. The result (-1, represented as `0xFFFFFFFF` in two’s complement) is stored in register R7.

---

### **Instruction 3: AND**

![Screenshot 2025-01-22 220539](https://github.com/user-attachments/assets/4f5a32d7-8b19-4fe3-aabe-5cae7b7e0b0a)


**Overview:**
- This instruction performs a bitwise AND operation between two register values and stores the result in a destination register.

**Execution Details:**
1. The instruction `AND R8, R1, R3` (0x0230A400) is fetched.
2. Register R1 holds the value 3 (`0011` in binary), and register R3 holds 1 (`0001` in binary).
3. The ALU executes the bitwise AND: `0011 & 0001 = 0001`.
4. The result (1) is stored in register R8.

---

### **Instruction 4: OR**

![Screenshot 2025-01-22 220625](https://github.com/user-attachments/assets/1eab13ee-4cb4-48e9-85db-4e95704b74d5)

**Overview:**
- This instruction performs a bitwise OR operation between two registers and stores the result in a destination register.

**Execution Details:**
1. The instruction `OR R9, R2, R5` is fetched.
2. The values in R2 and R5 are 2 (`0010`) and 5 (`0101`), respectively.
3. The ALU performs bitwise OR: `0010 | 0101 = 0111`.
4. The result (7) is stored in register R9.

---

### **Instruction 5: XOR**

![Screenshot 2025-01-22 224503](https://github.com/user-attachments/assets/08c73418-73fd-4f96-8355-57d06f3fc193)

**Overview:**
- This instruction performs a bitwise XOR operation between two registers and stores the result in a destination register.

**Execution Details:**
1. The instruction `XOR R10, R1, R4` is fetched.
2. The values in R1 and R4 are 1 (`0001`) and 4 (`0100`), respectively.
3. The ALU executes bitwise XOR: `0001 ^ 0100 = 0101`.
4. The result (5) is stored in register R10.

---

### **Instruction 6: SLT (Set Less Than)**

![Screenshot 2025-01-22 224702](https://github.com/user-attachments/assets/683dafb3-af55-409b-949e-89f8655a6296)

**Overview:**
- This instruction sets a register to 1 if one value is less than another; otherwise, it sets it to 0.

**Execution Details:**
1. The instruction `SLT R1, R2, R4` is fetched.
2. R2 holds 2, and R4 holds 4.
3. The ALU compares the values: `2 < 4` is true, so the result is 1.
4. The result (1) is stored in register R1.

---

### **Instruction 7: ADDI (Add Immediate)**

![image](https://github.com/user-attachments/assets/4317b78c-4289-42af-9d2a-e867f904b3f2)

**Overview:**
- The ADDI instruction adds an immediate value to a register and stores the result in a destination register.

**Execution Details:**
1. The instruction `ADDI R12, R4, 5` is fetched.
2. The value in R4 is 4.
3. The ALU performs the addition: `4 + 5 = 9`.
4. The result (9) is stored in register R12.

---

### **Instruction 8: BEQ (Branch if Equal)**

![image](https://github.com/user-attachments/assets/fae591e8-7c12-4cd5-8069-feab798b8710)


**Overview:**
- This instruction checks if two register values are equal and updates the program counter (PC) if the condition is met.

**Execution Details:**
1. The instruction `BEQ R0, R0, 15` is fetched.
2. The values in R0 and R0 are both 0.
3. Since they are equal, the PC is updated: `PC = 10 + 15 = 25 (0x19 in hexadecimal)`.

---

### **Instruction 9: BNE (Branch if Not Equal)**

![image](https://github.com/user-attachments/assets/6aa52a22-cf8b-4d19-9433-6bbc8038afd6)



**Overview:**
- This instruction checks if two register values are not equal and updates the PC accordingly.

**Execution Details:**
1. The instruction `BNE R0, R0, 20` is fetched.
2. The values in R0 and R0 are both 0.
3. Since they are equal, the branch is not taken, and the PC remains unchanged.

---

### Instruction 10. SLL

![image](https://github.com/user-attachments/assets/94fd2459-651d-456e-890d-6103cb0b658b)

### End of 4th task
</details>

------------------------------------------------------------------------------------------------------------------



<details>
<summary><b>Task 5:</b> Overview, Components Required, Circuit Connection, Pinout Diagram and Table for Pin connection required to build Gas Detector . </summary>


## Overview
This project is a gas leakage detection system using a CH32V00x microcontroller. The system continuously monitors a gas sensor (LPG sensor) and triggers an alarm (buzzer) and LED indicators when gas is detected. This implementation is useful for safety applications in homes and industries.

## Components Required
* CH32V00x Microcontroller (or equivalent)
* LPG Gas Sensor (e.g., MQ-2, MQ-5, or MQ-6)
* Buzzer
* LEDs (2 units)
* Resistors (if required for pull-up/pull-down circuits)
* Power Supply (3.3V or 5V, depending on the microcontroller and sensor requirements)
* Connecting Wires & Breadboard

## Table for Pin Connection
| **Component**         | **CH32V00x Pin** | **Mode**        | **Description**                          |
|----------------------|-----------------|----------------|------------------------------------------|
| Gas Sensor (Output)  | GPIOD Pin 2      | Input (Pull-up) | Reads gas sensor output                 |
| Buzzer              | GPIOD Pin 3      | Output         | Turns on when gas is detected          |
| LED 1 (Gas Alert)   | GPIOD Pin 4      | Output         | Lights up when gas is detected         |
| LED 2 (Safe Mode)   | GPIOD Pin 6      | Output         | Lights up when no gas is detected      |
| VCC                 | 3.3V / 5V        | Power          | Powers the circuit                     |
| GND                 | Ground           | Power          | Common ground connection |

## Pinout Diagram

![image](https://github.com/user-attachments/assets/72d0e029-075f-408e-b79f-adcf902cc391)


### End of 5th task
</details>

------------------------------------------------------------------------------------------------------------------

<details>
   <summary><b>Task 6: Working Code & short video demonstration .</summary>


## Code uploaded on the board
```
#include <ch32v00x.h>
#include <debug.h>

#define LED_GPIO_PORT GPIOD
#define LED_GPIO_PIN GPIO_Pin_4

#define LED2_GPIO_PORT GPIOD
#define LED2_GPIO_PIN GPIO_Pin_6


#define BUZZER_GPIO_PORT GPIOD
#define BUZZER_GPIO_PIN GPIO_Pin_3
#define GAS_SENSOR_GPIO_PIN GPIO_Pin_2 // LPG gas sensor output connected to GPIO Pin 2


// #define BLINKY_GPIO_PORT GPIOD
// #define BLINKY_GPIO_PIN GPIO_Pin_6
// #define BLINKY_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)

#define LED2_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)
#define LED_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)
#define BUZZER_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)
#define GAS_SENSOR_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)

// Function prototypes
//(void) attribute((interrupt("WCH-Interrupt-fast")));
//void HardFault_Handler(void) attribute((interrupt("WCH-Interrupt-fast")));
void Delay_Init(void);
void Delay_Ms(uint32_t n);

// Main function
int main(void)
{
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_2); // Configure NVIC priority grouping
    SystemCoreClockUpdate(); // Update system core clock
    Delay_Init(); // Initialize delay function

    // GPIO configuration structure
    GPIO_InitTypeDef GPIO_InitStructure = {0};

    // Enable clock for GPIO port
    LED_CLOCK_ENABLE;
	LED2_CLOCK_ENABLE;
    BUZZER_CLOCK_ENABLE;
    GAS_SENSOR_CLOCK_ENABLE;


	// BLINKY_CLOCK_ENABLE;
	// GPIO_InitStructure.GPIO_Pin = BLINKY_GPIO_PIN;
	// GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	// GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	// GPIO_Init(BLINKY_GPIO_PORT, &GPIO_InitStructure);

    // Configure GPIO pin for LED
    GPIO_InitStructure.GPIO_Pin = LED_GPIO_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Output push-pull mode
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz; // GPIO speed
    GPIO_Init(LED_GPIO_PORT, &GPIO_InitStructure);

    // Configure GPIO pin for LED2
    GPIO_InitStructure.GPIO_Pin = LED2_GPIO_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Output push-pull mode
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz; // GPIO speed
    GPIO_Init(LED2_GPIO_PORT, &GPIO_InitStructure);

	
	// Configure GPIO pin for buzzer
    GPIO_InitStructure.GPIO_Pin = BUZZER_GPIO_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Output push-pull mode
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz; // GPIO speed
    GPIO_Init(BUZZER_GPIO_PORT, &GPIO_InitStructure);

    // Configure GPIO pin for gas sensor input
    GPIO_InitStructure.GPIO_Pin = GAS_SENSOR_GPIO_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU; // Input mode with pull-up resistor
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    // Initialize UART for debugging
    USART_Printf_Init(115200); // Initialize UART with baud rate 115200
    printf("System Initialized\n");

    // Main loop
	//uint8_t ledState = 0;
    while (1)

    {	
		// GPIO_WriteBit(BLINKY_GPIO_PORT, BLINKY_GPIO_PIN, ledState);
		// ledState ^= 1; // invert for the next run
        // Read gas sensor status
        uint8_t gasStatus = !GPIO_ReadInputDataBit(GPIOD, GAS_SENSOR_GPIO_PIN);
        printf("Gas Sensor Status: %d\n", gasStatus);

        // Control the buzzer and LED based on gas sensor output
        if (gasStatus == 1) // Gas sensor detected gas leak
        {
            GPIO_WriteBit(BUZZER_GPIO_PORT, BUZZER_GPIO_PIN,  Bit_SET); // Turn on buzzer
            GPIO_WriteBit(LED_GPIO_PORT, LED_GPIO_PIN, SET); // Turn on LED
			GPIO_WriteBit(LED2_GPIO_PORT, LED2_GPIO_PIN, RESET); // Turn off LED
            printf("Gas Detected! Buzzer ON, LED ON\n");
        }
        else
        {
            GPIO_WriteBit(BUZZER_GPIO_PORT, BUZZER_GPIO_PIN, Bit_RESET); // Turn off buzzer
            GPIO_WriteBit(LED_GPIO_PORT, LED_GPIO_PIN, RESET); // Turn off LED
            GPIO_WriteBit(LED2_GPIO_PORT, LED2_GPIO_PIN, SET); // Turn on LED
			printf("No Gas. Buzzer OFF, LED OFF\n");
        }

        Delay_Ms(250); // Delay for debouncing and visualization
    }
}

// // Non-Maskable Interrupt handler
// void NMI_Handler(void) {}

// // Hard Fault handler
// void HardFault_Handler(void)
// {
//     while (1) {}
// }

// Delay initialization function
// void Delay_Init(void)
// {
//     SysTick_Config(SystemCoreClock / 1000); // Configure SysTick for 1ms ticks
// }

// // Millisecond delay function
// void Delay_Ms(uint32_t n)
// {
//     while (n--)
//     {
//         while (!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk)) {} // Wait for SysTick flag
//     }
// }
```
# short video demonstration 
Project Simulation Video:https://drive.google.com/file/d/1HxW0zdGNbEvsLwUF1x1cixc0A6dxaCDE/view?usp=drivesdk

### End of 6th task
</details>

------------------------------------------------------------------------------------------------------------------
