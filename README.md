# RISC-V Single-Cycle Architecture with CSR

This repository contains a simple implementation of a **RISC-V single-cycle processor architecture** with support for **Control and Status Registers (CSR)**. It is designed to help students and enthusiasts understand the working of RISC-V processors, instruction execution, exception handling, and CSR operations.

---

# Features

- Implements **RV32I base integer instruction set**.
- Single-cycle datapath architecture (all instructions complete in one clock cycle).
- CSR (Control and Status Register) support:
  - Machine-mode CSRs like `mstatus`, `mtvec`, `mepc`, `mcause`.
  - CSR read and write instructions.
- Exception and interrupt handling.
- Simple memory and register file implementation.
- Written in **Verilog / VHDL** (choose based on your implementation).

---

## Architecture Overview

The single-cycle RISC-V processor executes every instruction in one clock cycle. Its major components include:

1. **Program Counter (PC)**: Holds the address of the next instruction.
2. **Instruction Memory**: Stores RISC-V instructions.
3. **Register File**: Contains 32 general-purpose registers.
4. **ALU (Arithmetic Logic Unit)**: Performs arithmetic and logical operations.
5. **Data Memory**: Stores and loads data for memory instructions.
6. **Control Unit**: Generates control signals based on opcode and funct3/funct7 fields.
7. **CSR Module**: Handles Control and Status Registers, allowing privileged operations.
8. **Exception/Interrupt Handling**: Updates CSRs and program flow during exceptions.

### Datapath

The datapath of the single-cycle processor consists of:

- Instruction fetch from memory using PC.
- Decoding instruction fields (opcode, rs1, rs2, rd, imm).
- ALU operations or CSR read/write operations.
- Memory access if required.
- Write-back to the register file.
- PC update (next instruction or exception handler address).

---

## Supported Instructions

- **Integer(Ray) instructions**: ADD, SUB, AND, OR, XOR, SLL, SRL, SRA, SLT, SLTU
- **Immediate instructions**: ADDI, ANDI, ORI, XORI, SLTI, SLTIU, SLLI, SRLI, SRAI
- **Load/Store instructions**: LB, LH, LW, LBU, LHU, SB, SH, SW
- **Branch instructions**: BEQ, BNE, BLT, BGE, BLTU, BGEU
- **Jump instructions**: JAL, JALR
- **CSR instructions**: CSRRW, CSRRS, CSRRC, CSRRWI, CSRRSI, CSRRCI

---

## Exception & CSR Handling

The processor supports machine-mode exceptions and interrupts:

- **Exceptions**: Illegal instructions, misaligned access, ecall/ebreak.
- **CSR Updates**: During exceptions, `mepc` stores the return address, `mcause` stores the cause, and `mtvec` holds the handler address.
- **CSR Instructions**: Allow reading, writing, or modifying CSR registers directly.

---

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/Moizadlh/RISC-V_SingleCycleWithCSR.git
2. Open in VSCode

    --Open the project folder in Visual Studio Code.

    --Ensure you have a SystemVerilog extension installed (for syntax highlighting and code navigation).

3. Compile the Design

    --Use your preferred HDL simulator (ModelSim, Vivado, or others) to compile the SystemVerilog files.

4. Run the Simulation

    --Execute the provided testbench to simulate the processor.

    --This will demonstrate instruction execution, CSR operations, and exception handling.

5. Visualize Waveforms

    --Open the generated waveform file in GTKWave to observe signals and processor behavior.

6. Experiment

    --Modify or add RISC-V instructions in the testbench to explore:

        ALU operations
        
        Load/Store instructions
        
        Branches and jumps
        
        CSR read/write and exception handling
