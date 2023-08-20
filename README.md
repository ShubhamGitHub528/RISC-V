# RISC-V

### Day 1: Introduction to RISC-V and GNU compiler toolchain

<details>
<summary>Introduction to RISC-V Basic keywords</summary>
 <br />  
  
*RISC-V (pronounced "risk-five") is an open-source instruction set architecture (ISA) designed for computer processors. It has gained significant attention in recent years due to its simplicity, flexibility, and potential for customization. Here are some basic keywords to help you understand RISC-V*

RISC-V's basic keywords:

**RISC-V:** Open-source computer architecture with simple instructions. <br />
**ISA:** Instruction Set Architecture defines processor instructions. <br />
**Registers:** Temporary data storage in the processor. <br />
**Load-Store:** Instructions access memory via loads and stores. <br />
**Privilege Levels:** User, supervisor, and machine modes. <br />
**Formats:** Instruction types like R, I, S, B, U, J. <br />
**Pipeline:** Concurrent instruction execution stages. <br />
**Branch:** Instructions for decision-making and jumping. <br />
**Immediate:** Constants embedded in instructions. <br />
**Opcode:** Binary code for specifying operations. <br />
**Assembly:** Human-readable machine code representation. <br />
**Toolchain:** Software tools for RISC-V development. <br />
**ABI:** Interface for binary-level software interaction. <br />
**CISC vs. RISC:** Simple vs. complex instruction architectures. <br />
</details>

<details>
<summary>Labwork for RISC-V software toolchain</summary>
  
**C program to compute Sum from 1 to N.**
  
```
#include<stdio.h>

int main()
{
int i,sum = 0,n = 100;
for(i= 1;i <= n; ++i)
{
sum += i;
}
printf("sum of numbers from 1 to %d is %d\n", n,sum);

}
```

**Risc-V Compile and Disassemble**

![Screenshot from 2023-08-19 13-15-52](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/0119fafb-4fbd-4d02-b269-be1e38270b92)

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.
```

![Screenshot from 2023-08-19 13-16-14](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/881d5958-2a5c-4285-b7d4-3d3cc63b8284)
**Spike simulation and Debug**
for output using spike command

```
spike -d pk sum1ton.o
```

![Screenshot from 2023-08-19 13-20-13](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d05009a6-c6a0-49c8-9ab5-506168bece36)

</details>

<details>
<summary>Integer number Representation</summary>
  
*Unsigned integers cover a larger positive range, while signed integers have both positive and negative values within a more limited range due to the need to represent the sign bit.*

**64-Bit Number system for Unsigned Number**
*    Range: 0 to 18,446,744,073,709,551,615 (2^64 - 1)
*    All 64 bits are used to represent the magnitude of the number.
*    The leftmost (most significant) bit is the "sign bit" for determining whether the number is positive or negative.
*    Since unsigned integers don't have a sign bit, all 64 bits contribute to the value.
  ![Screenshot from 2023-08-19 15-01-44](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e899be33-7613-4410-9795-2c6c7bb8ea1f)

**64-Bit Number system for Signed Number**

*    Range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
*    The leftmost (most significant) bit is the sign bit.
*    0 in the sign bit represents a positive number, and 1 represents a negative number.
*    The remaining 63 bits are used to represent the magnitude using the two's complement representation.
*    To convert from a negative value to its two's complement, invert all the bits and add 1.

![Screenshot from 2023-08-19 15-35-19](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/35de496b-e5d2-47f3-9836-9ae21dc3fada)
  
</details>

### Day 2: Introduction to ABI and Basic verification flow

<details>
<summary>Application Binary Interface</summary>
  </br>
  
**Introduction to Application Binary Interface**

*An Application Binary Interface (ABI) is a set of rules and conventions that define how different software components interact with each other at the binary level. It establishes a standard for communication between various parts of a software system, such as libraries, applications, and the operating system. The ABI ensures compatibility and interoperability, allowing programs compiled on different systems to work together seamlessly.*

![Screenshot from 2023-08-19 16-18-44](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/75859d7c-46f1-4f92-b587-081993b5a80e)
</br></br>
**Memory allocation For Double words**
*Allocating memory for double words means reserving space in units of two processor words. Each word is typically 4 or 8 bytes. This approach helps maintain memory alignment, essential for efficient memory access and performance. Proper alignment follows the word size and ensures data starts at addresses divisible by the word size.*
</br></br>
**Load Store and Add Instructions with Examples**
Load and Store Instructions:
Load and store instructions are fundamental in RISC architectures like RISC-V. They handle data movement between memory and registers.

*    Load: Moves data from memory to registers. Examples are LW (Load Word) and LD (Load Doubleword), which fetch 32 or 64 bits respectively.

*    Store: Moves data from registers to memory. SW (Store Word) and SD (Store Doubleword) are common examples.

These instructions are essential for accessing data stored in memory and interacting with it.

Add Instructions:
Add instructions perform addition operations in processors.

*    ADD: Adds two values and stores the result in a destination register.

*    ADDI: Adds an immediate value to the value in a register, storing the result in a destination register.

*    ADDU: Unsigned version of ADD, which ignores overflow.

These instructions are core arithmetic operations and are used for various calculations in programs.
</br>

![Screenshot from 2023-08-19 18-20-53](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/f160abd9-b232-4900-bc99-eae8872dba84)

</br>

**32-Bit registers and their respective API function calls**
In a 32-bit architecture, registers are data storage locations within the processor that are directly accessible by the CPU. They are used for temporary data storage during program execution. 

</details>

<details>
<summary>Lab work using ABI function calls</summary>
</br>
  
**Study New Algorithm for Sum 1 to N Using ASM and Simulate New C program with Fumction Call**
  
![Screenshot from 2023-08-19 19-27-53](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/dc2e72f4-4f9b-4ede-99a3-d4a9951582bb)

  ![Screenshot from 2023-08-19 19-28-07](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/2790530c-a99b-40bc-8f72-86e7945851dd)

</br>

</details>

### Day 3: Digital Logic with TL-Verilog and Makerchip.

<details>
<summary> Combinational Logic </summary>
</br>
 
**Logic Gates**
Logic gates are fundamental building blocks of digital circuits and are used to perform logical operations on binary inputs (0s and 1s). These gates are the foundation of digital computing and are used to create more complex functions and operations. There are several types of logic gates, each with its own specific behavior. 

**Inverter**
![Screenshot from 2023-08-20 17-34-36](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/7209b8b6-b3d2-41bd-bad0-32554ff02585)

**And**
![Screenshot from 2023-08-20 17-41-01](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/f040b28f-2f2f-40cc-adac-92af2a936ea0)


**Vector**
![Screenshot from 2023-08-20 17-52-58](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/b03ed31c-73e1-4048-b558-bb167e2f0759)

**Mux**
![Screenshot from 2023-08-20 18-03-47](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/15692be1-9b93-4691-8355-b82efadc3987)
![Screenshot from 2023-08-20 18-03-54](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/af31a238-22cd-4e0b-ad49-23722c754b01)

**Combinational Calculator**

![Screenshot from 2023-08-20 18-05-37](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/7a871711-f1f1-47a1-9617-db3991c9a8b6)
![Screenshot from 2023-08-20 19-36-17](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/e3401130-31ce-4fc2-a936-ec1f03ccc68e)

</details>

<details>
<summary> Sequential Logic </summary>
</br>
 
**Febonacci Series**
![Screenshot from 2023-08-20 19-50-16](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/5ddc138d-8a63-4453-946a-95f0d6690bec)
![Screenshot from 2023-08-20 19-54-06](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/ad16a09a-f407-4b06-a208-aff9e8c79901)

**Counter**
![Screenshot from 2023-08-20 19-56-53](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/63043ce7-f884-473a-a698-b465f801a06d)

**Sequential Calculator**
![Screenshot from 2023-08-20 20-03-52](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/f7bb1080-415b-4f38-b2d5-4acb0096cc8b)
![Screenshot from 2023-08-20 21-27-29](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/b6427f4f-d8b2-44fd-befe-0af471bf4187)


</details>

<details>
<summary> Pipelined Logic </summary>
</br>
 
**Error Conditions within Computation Pipeline**

![Screenshot from 2023-08-20 22-32-26](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/4605a30a-731f-436f-b39b-429bbb720520)

**Counter & Calculator**
![Screenshot from 2023-08-20 22-48-14](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/9003ee00-d348-4f41-8449-0760b72ca39e)

**2-Cycle Calculator**
![Screenshot from 2023-08-20 23-14-54](https://github.com/ShubhamGitHub528/RISC-V/assets/140998623/30253c93-6270-49ca-a32d-ff4a1811b96b)


</details>

<details>
<summary> Validity </summary>
</br>


</details>
