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
	

###SPIKE in RISCV?
* Spike is a free, open-source C++ simulator for the RISC-V ISA that models a RISC-V core and cache system. It can be used to run programs and a Linux kernel, and can be a starting point for running software on a RISC-V target.

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




