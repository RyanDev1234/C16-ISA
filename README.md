# C16-ISA  ![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
# ⚡ C16 — Compact 16 Instruction Set Architecture

**C16 — Compact 16 Instruction Set Architecture** is a minimal ISA with exactly **16 instructions**.  
It is designed to be **simple, easy to decode, and compiler‑friendly**, while still supporting **bare‑metal C programming**.  
The ISA uses a clean **4‑bit opcode space** (0000–1111).

---

## ✨ Instruction Categories

### 1. Memory Access
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x0    | 0000   | LD R, [Rp]  | Load from memory at register pointer into R |
| 0x1    | 0001   | STR R, [Rp] | Store R into memory at register pointer |

### 2. Data Movement
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x2    | 0010   | MOV R1, R2 | Copy register contents |
| 0x3    | 0011   | IMM R, #const | Load immediate constant into register |

### 3. Arithmetic
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x4    | 0100   | ADD R1, R2 | R1 = R1 + R2 |
| 0x5    | 0101   | SUB R1, R2 | R1 = R1 - R2 |
| 0x6    | 0110   | MUL R1, R2 | R1 = R1 × R2 |

### 4. Logic
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x7    | 0111   | AND R1, R2 | Bitwise AND |
| 0x8    | 1000   | OR R1, R2  | Bitwise OR |
| 0x9    | 1001   | XOR R1, R2 | Bitwise XOR |

### 5. Control Flow
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0xA    | 1010   | JMP R       | Jump to address in register |
| 0xB    | 1011   | BEQ R1, R2, addr | Branch if R1 == R2 |
| 0xC    | 1100   | BNE R1, R2, addr | Branch if R1 != R2 |
| 0xD    | 1101   | BZ R, addr  | Branch if R == 0 |
| 0xE    | 1110   | CALL R      | Call subroutine at address in register |
| 0xF    | 1111   | RET         | Return from subroutine |

---

## 🏷️ Instruction Set (Binary Opcodes)

| Opcode (Binary) | Opcode (Hex) | Mnemonic        | Operands        | Description |
|-----------------|--------------|-----------------|-----------------|-------------|
| `0000`          | 0x0          | **LD R, [Rp]**  | R, Rp           | Load word from memory at register pointer Rp into R |
| `0001`          | 0x1          | **STR R, [Rp]** | R, Rp           | Store word from R into memory at register pointer Rp |
| `0010`          | 0x2          | **MOV R1, R2**  | R1, R2          | Copy register contents |
| `0011`          | 0x3          | **IMM R, #const** | R, const      | Load immediate constant into register |
| `0100`          | 0x4          | **ADD R1, R2**  | R1, R2          | Add registers (R1 = R1 + R2) |
| `0101`          | 0x5          | **SUB R1, R2**  | R1, R2          | Subtract registers (R1 = R1 - R2) |
| `0110`          | 0x6          | **MUL R1, R2**  | R1, R2          | Multiply registers |
| `0111`          | 0x7          | **AND R1, R2**  | R1, R2          | Bitwise AND |
| `1000`          | 0x8          | **OR R1, R2**   | R1, R2          | Bitwise OR |
| `1001`          | 0x9          | **XOR R1, R2**  | R1, R2          | Bitwise XOR |
| `1010`          | 0xA          | **JMP R**       | R               | Jump to address stored in register |
| `1011`          | 0xB          | **BEQ R1, R2, addr** | R1, R2, addr | Branch if R1 == R2 |
| `1100`          | 0xC          | **BNE R1, R2, addr** | R1, R2, addr | Branch if R1 != R2 |
| `1101`          | 0xD          | **BZ R, addr**  | R, addr         | Branch if register == 0 |
| `1110`          | 0xE          | **CALL R**      | R               | Call subroutine at address in register |
| `1111`          | 0xF          | **RET**         | –               | Return from subroutine |

---

## 📜 Encoding Notes
- **Opcode field**: 4 bits (selects one of 16 instructions)  
- **Register fields**: 4 bits each (up to 16 registers)  
- **Immediate/addr fields**: variable length depending on instruction format  
- **Instruction word size**: typically 16 bits for compactness  

---

## ✅ Purpose
C16 is designed as a **minimal yet complete ISA** for learning, experimentation, and bare‑metal C programming.  
Its simplicity makes it ideal for teaching computer architecture, building emulators, or experimenting with compiler backends.

## 🙌 Credits
C16 ISA was created by RyanDev1234.  
Please retain attribution when modifying or redistributing.

