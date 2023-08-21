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
 
**2- Cycle Calculator with Validity**
![Screenshot from 2023-08-21 10-47-23](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/34015987-c89a-4dec-b859-167849972431)
![Screenshot from 2023-08-21 11-56-26](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/412eb666-377a-4e3e-8061-78eb140cf0e7)

**Calculator with Single Value Memory** 
![Screenshot from 2023-08-21 11-59-56](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/650cb09e-df16-498a-a794-c81150ac20b4)
![Screenshot from 2023-08-21 12-00-19](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/065e72d7-d369-42ac-8550-6e8e70640062)


</details>

### Day4: Basic RISC-V CPU micro-architecture.
</br>

<details>
<summary> RISC-V CPU</summary>
</br>

![Screenshot from 2023-08-21 22-07-45](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/ca0a9be5-4796-41bb-b231-361db7e6e28c)


**1. Program Counter (PC)** - The program counter is a special register in a CPU that keeps track of the memory address of the next instruction to be fetched and executed. It is incremented as instructions are fetched, and it provides the address to the instruction memory for fetching the next instruction in the program.

**2. Instruction Decoder** - The instruction decoder is a circuit within the CPU that interprets the machine instructions fetched from memory. It decodes the binary representation of the instruction and generates control signals that govern the operation of other components in the CPU to execute the instruction.

**3. Instruction Memory** - The instruction memory is a storage component that holds the machine instructions of a program. It is typically read-only and stores the binary instructions that the CPU fetches and decodes. The program counter provides the address to the instruction memory for fetching the next instruction.

**4. Data Memory** - The data memory is a storage component used to store data that is manipulated by instructions during program execution. Unlike instruction memory, data memory can be both read from and written to. It holds variables, data arrays, and other information that the program uses during its execution.

**5. ALU (Arithmetic Logic Unit)** - The ALU is a fundamental digital circuit within the CPU that performs arithmetic and logical operations on data. It can perform tasks such as addition, subtraction, multiplication, division, bitwise operations (AND, OR, XOR), and comparisons. The ALU generates results that are used in various computations specified by the instructions.

**6. Read Register File** - The read register file is a component that stores a set of registers used to hold data during the execution of instructions. Instructions often involve reading data from these registers. The instruction specifies which registers to read, and the data from these registers can be used as operands for operations performed by the ALU or other components.

**7. Write Register File** - The write register file is responsible for storing the results of operations back into registers. After an instruction is executed, the result is often written back to the register file. This ensures that the updated data is available for subsequent instructions.

These components work together to execute machine instructions in a CPU. The program counter guides the instruction fetch process, the instruction decoder interprets instructions, the ALU performs computations, the register files hold data, and the memory components provide data storage and access. This orchestration allows a CPU to carry out the tasks required by a program's instructions.

</details>

<details>
<summary>Fetch And Decoder</summary>

#### Fetch

**Template For Running Viz:**

```
\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;



      // YOUR CODE HERE
      // ...

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      //m4+imem(@1)    // Args: (read stage)
      //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)
      //m4+myth_fpga(@0)  // Uncomment to run on fpga

   //m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule
```

**L1 - Implementation Plan and Lab for PC**
![Screenshot from 2023-08-22 00-08-19](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/30fc43ad-fd1d-4065-b113-72b537a5659f)
![Screenshot from 2023-08-21 14-40-41](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/79905e9b-cb1e-447f-ba69-000124897741)
![Screenshot from 2023-08-21 14-53-00](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/1809b4c3-40e5-40a4-94ab-790d4d914fec)
**L2 - Lab for instruction fetch logic**

![Screenshot from 2023-08-22 00-08-43](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/33f1492f-eab8-4466-9f39-f4f9b94282b5)
Fetch Block diagram 
![Screenshot from 2023-08-21 20-40-39](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/adf9ffaf-9cf4-4e2d-818e-8768b8a4e095)
Output:
![Screenshot from 2023-08-21 20-51-09](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/154ee8c5-4aad-44f9-b968-36aeb6acaaa4)
Correct fetch Block Diagram :
![Screenshot from 2023-08-21 21-40-46](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/fc9a44df-90ec-4e32-9b63-9b593dcc0941)
Via
![Screenshot from 2023-08-21 21-44-00](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/76743a60-f139-4c43-83ff-c5a4ff1219ab)

#### Decoder:


**L3 - Lab for RV instruction types IRSBJU Decode Logic**
![Screenshot from 2023-08-22 00-08-59](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/fb163a32-b6c3-4a9f-b91a-101897ab04dd)

![Screenshot from 2023-08-22 00-32-15](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d511836e-7303-4631-87b4-7a7edc0a0fe5)

**L4 - Lab for instruction immediate decode logic for RV ISBUJ**
![Screenshot from 2023-08-22 00-09-30](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d0b74a04-0bbf-4ea3-b9d2-a7bf481ae355)

![Screenshot from 2023-08-22 00-32-36](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/ae74fa9f-427a-477f-a644-0315a40ad34b)

**L5 - Lab to decode other fields of Instruction of RV ISBUJ**
![Screenshot from 2023-08-22 00-09-50](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/384cb428-bbd2-4545-be52-f1cb304a33d5)
![Screenshot from 2023-08-22 00-32-47](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/f3fdf5bf-712d-4a92-aa12-f6d4da105f25)

**L6 - Lab to decode instruction fields based on Instruction type RV ISBUJ**
![Screenshot from 2023-08-22 00-10-00](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/396c3e8d-c9cb-455a-a375-9f1363e62882)

![Screenshot from 2023-08-22 00-32-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/60b71e9e-1762-4e06-a71b-a0d683328b58)

**L7 - Lab to decode individual Instruction**
![Screenshot from 2023-08-22 00-10-20](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/3369c564-87fe-4245-ba98-964663e552c8)
![Screenshot from 2023-08-22 00-33-09](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/9ac0557c-00ca-4008-82c4-0ed8e1b37734)



</details>


<details>
  <summary>
    RV-D4SK3 - RISCV Control Logic 
  </summary>

**L1 - Lab for Register file read -1**
![Screenshot from 2023-08-22 00-10-55](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/7a2c38f6-20e7-40a7-8269-2d03ce1570bc)
![Screenshot from 2023-08-22 00-38-33](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/2bce4ba2-d585-42ca-804d-0d67857ef05c)

**Lab for Register file read -2**
![Screenshot from 2023-08-22 00-11-16](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/6d5282fb-1da5-47c3-b557-72c0189743a3)

![Screenshot from 2023-08-22 00-38-49](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/267fffcb-4a75-4be4-bd0b-4c7bffd9d9d2)

**L3 - Lab for ALU operations**
![Screenshot from 2023-08-22 00-11-32](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d63685bd-59ec-4e93-bd63-f7bc46a86ffe)

![Screenshot from 2023-08-22 00-39-01](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/1cd88720-24ce-442b-9b91-7f7039f0576f)

**L4 - Lab for Register file write** 
![Screenshot from 2023-08-22 00-11-38](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/59f67eda-e77d-4de6-8524-8879d81db90a)
![Screenshot from 2023-08-22 00-39-16](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/8700881e-8b34-4e46-921f-a5fb3b57d540)

**L5 - Concept of array and Rgister file details**
![Screenshot from 2023-08-22 00-11-48](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/424d6240-c7c5-4332-801d-0d4348e27387)

![Screenshot from 2023-08-22 00-39-47](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/126ca197-6f8e-457e-8a93-bc395b3b744e)

**L6 - Lab for implementing branch Instructions**
![Screenshot from 2023-08-22 00-12-08](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/b14cfcd4-5d3a-4be6-b931-16579ebc7310)


**L7 - Lab fpr completing branch instructions implementations**
![Screenshot from 2023-08-22 00-12-19](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c1475b36-02e7-4ced-871d-9ac51cff15a6)
![Screenshot from 2023-08-22 00-40-16](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/2845cc10-0808-4351-bca8-03d80daabfda)

**L8 - Lab to create simple testbench**
![Screenshot from 2023-08-22 00-12-31](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e4b9243d-dfda-4cd4-b898-02ee75d4cb96)

![Screenshot from 2023-08-22 00-42-41](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/1820b072-7fe8-4cef-9399-57d09542b0d3)


</details>


## DAY-5 Complete Pipelined RISCV CPU Microarchitecture



<details>
  <summary>
    RV-D5SK1 - Pipelining the CPU  
  </summary>

  ## RV-D5SK1 - L1 - Introduction to control flow hazard and read after write hazard
  ## RV-D5SK1 - L2 - Create 3 cycle valid signal
  ## RV-D5SK1 - L3 - Code 3 cycle RISCV architecture to take care of invalid signal
  ## RV-D5SK1 - L4 - To modify 3 cycle RISCV to distribute logic 

</details>


<details>
  <summary>
    RV-D5SK2 - Solution to Pipeline Hazard
  </summary>


## RV-D5SK2 - L1 - Register File Bypass to address RD after WR hazard
## RV-D5SK2 - L2 - Braches to correct branch target path
## RV-D5SK2 - L3 - Complete instuction decode 
## RV-D5SK2 - L4 - Code complete ALU
</details>

<details>
  <summary>
    RV-D5SK3 - Load Store Instruction and completing RISCV CPU
  </summary>

## RV-D5SK3 - L1 - Introduction and Lab to redirect load
## RV-D5SK3 - L2 - Load data from Memory to Rgister file
## RV-D5SK3 - L3 - Add loads and stores to test program
## RV-D5SK3 - L4 - Add control logic for JUMP instructions
## RV-D5SK3 - L5 - Wrap up 



