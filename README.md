# ⚡ C16 — Compact 16 Instruction Set Architecture

**C16 — Compact 16 Instruction Set Architecture** is a minimal ISA with exactly **16 instructions**.  
It is designed to be **simple, easy to decode, and compiler‑friendly**, while still supporting **bare‑metal C programming**.  
The ISA uses a clean **4‑bit opcode space** (0000–1111).

---

## ✨ Instruction Categories

### 1. Memory Access
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x0    | 0000   | LDR R, [Rp]  | Load from memory at register pointer into R |
| 0x1    | 0001   | STR R, [Rp]  | Store R into memory at register pointer |

### 2. Data Movement
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x2    | 0010   | MOV R1, R2 | Copy register contents |
| 0x3    | 0011   | LDI R, #const | Load immediate constant into register |

### 3. Arithmetic
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x4    | 0100   | ADD R1, R2 | R1 = R1 + R2 (Flags updated) |
| 0x5    | 0101   | SUB R1, R2 | R1 = R1 - R2 (Flags updated) |
| 0x6    | 0110   | MUL R1, R2 | R1 = R1 × R2 (Flags updated) |
| 0x7    | 0111   | DIV R1, R2 | R1 = R1 ÷ R2 (Flags updated) |

### 4. Logic
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0x8    | 1000   | AND R1, R2 | Bitwise AND (Flags updated) |
| 0x9    | 1001   | OR R1, R2  | Bitwise OR (Flags updated) |
| 0xA    | 1010   | XOR R1, R2 | Bitwise XOR (Flags updated) |

### 5. Control Flow & System
| Opcode | Binary | Mnemonic | Description |
|--------|--------|----------|-------------|
| 0xB    | 1011   | JMP R       | Jump to address in register |
| 0xC    | 1100   | BRH cond, R | Branch on condition (EQL, NEQ, GT, LT, GEQ, LEQ) to address in register |
| 0xD    | 1101   | PUSH R      | Push register value into stack memory |
| 0xE    | 1110   | POP R       | Pop value from stack memory into register |
| 0xF    | 1111   | INT n       | Software interrupt (trigger IRQn handler) |

---

## 🏷️ Instruction Set (Binary Opcodes)

| Opcode (Binary) | Opcode (Hex) | Mnemonic        | Operands        | Description |
|-----------------|--------------|-----------------|-----------------|-------------|
| `0000`          | 0x0          | **LDR R, [Rp]**  | R, Rp           | Load word from memory at register pointer Rp into R |
| `0001`          | 0x1          | **STR R, [Rp]** | R, Rp           | Store word from R into memory at register pointer Rp |
| `0010`          | 0x2          | **MOV R1, R2**  | R1, R2          | Copy register contents |
| `0011`          | 0x3          | **LDI R, #const** | R, const      | Load immediate constant into register |
| `0100`          | 0x4          | **ADD R1, R2**  | R1, R2          | Add registers (Flags updated) |
| `0101`          | 0x5          | **SUB R1, R2**  | R1, R2          | Subtract registers (Flags updated) |
| `0110`          | 0x6          | **MUL R1, R2**  | R1, R2          | Multiply registers (Flags updated) |
| `0111`          | 0x7          | **DIV R1, R2**  | R1, R2          | Divide registers (Flags updated) |
| `1000`          | 0x8          | **AND R1, R2**  | R1, R2          | Bitwise AND (Flags updated) |
| `1001`          | 0x9          | **OR R1, R2**   | R1, R2          | Bitwise OR (Flags updated) |
| `1010`          | 0xA          | **XOR R1, R2**  | R1, R2          | Bitwise XOR (Flags updated) |
| `1011`          | 0xB          | **JMP R**       | R               | Jump to address stored in register |
| `1100`          | 0xC          | **BRH cond, R** | cond, R         | Branch on condition (EQL, NEQ, GT, LT, GEQ, LEQ) to address in register |
| `1101`          | 0xD          | **PUSH R**      | R               | Push register value into stack memory |
| `1110`          | 0xE          | **POP R**       | R               | Pop value from stack memory into register |
| `1111`          | 0xF          | **INT n**       | n               | Software interrupt (trigger IRQn handler) |

---

## 📜 Encoding Notes
- **Opcode field**: 4 bits (selects one of 16 instructions)  
- **Register fields**: 6 bits each (up to 64 registers)  
- **Immediate/addr fields**: variable length depending on instruction format  
- **Instruction word size**: typically 16 bits for compactness  

---

## ✅ Purpose
C16 is designed as a **minimal yet complete ISA** for learning, experimentation, and bare‑metal C programming.  
Its simplicity makes it ideal for teaching computer architecture, building emulators, or experimenting with compiler backends.
