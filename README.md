# Samsung-RISC-V
NAME: Rohan V Poorma  
College: KLE Institute of Technology  
EmailID:rohanpoorma7@gmail.com   
Github:https://github.com/phoenix-chipdesign   


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
