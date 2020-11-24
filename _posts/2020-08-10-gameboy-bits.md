---
layout: post
title: "Gameboy opcode reference by bit patterns"
author: "Bruno Fusieger"
categories: "Reference"
---

This reference is based on several bit patterns found on the Gameboy opcode matrix. But before presenting the data we need to stablish some conventions:

- The opcode bits are separated in 3 octal numbers (x, y, z) where x = MSB and Z = LSB
- The tables are categorized based on a constant value, like z = 0

## X=0 and Z=0

Relative jumps and others

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| NOP        | 00 000 000 | 0x00 |
| LD (nn),SP | 00 001 000 | 0x08 |
| STOP       | 00 010 000 | 0x10 |
| JR n       | 00 011 000 | 0x18 |
| JR NZ,n    | 00 100 000 | 0x20 |
| JR Z,n     | 00 101 000 | 0x28 |
| JR NC,n    | 00 110 000 | 0x30 |
| JR C,n     | 00 111 000 | 0x38 |

---

## X=0 and Z=1

Loads and additions of 16 bit registers with immediate short

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD BC,nn  | 00 000 001 | 0x01 |
| ADD HL,BC | 00 001 001 | 0x09 |
| LD DE,nn  | 00 010 001 | 0x11 |
| ADD HL,DE | 00 011 001 | 0x19 |
| LD HL,nn  | 00 100 001 | 0x21 |
| ADD HL,HL | 00 101 001 | 0x29 |
| LD SP,nn  | 00 110 001 | 0x31 |
| ADD HL,SP | 00 111 001 | 0x39 |

---

## X=0 and Z=2

Loads using 16 bit registers

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| LD (BC),A  | 00 000 010 | 0x02 |
| LD A,(BC)  | 00 001 010 | 0x0A |
| LD (DE),A  | 00 010 010 | 0x12 |
| LD A,(DE)  | 00 011 010 | 0x1A |
| LD (HL+),A | 00 100 010 | 0x22 |
| LD A,(HL+) | 00 101 010 | 0x2A |
| LD (HL-),A | 00 110 010 | 0x32 |
| LD A,(HL-) | 00 111 010 | 0x3A |

---

## X=0 and Z=3

Increment/Decrement operations in 16 bit registers

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| INC BC   | 00 000 011 | 0x03 |
| DEC BC   | 00 001 011 | 0x0B |
| INC DE   | 00 010 011 | 0x13 |
| DEC DE   | 00 011 011 | 0x1B |
| INC HL   | 00 100 011 | 0x23 |
| DEC HL   | 00 101 011 | 0x2B |
| INC SP   | 00 110 011 | 0x33 |
| DEC SP   | 00 111 011 | 0x3B |

---

## X=0 and Z=4

Increment operations in 8 bit registers

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| INC B    | 00 000 100 | 0x04 |
| INC C    | 00 001 100 | 0x0C |
| INC D    | 00 010 100 | 0x14 |
| INC E    | 00 011 100 | 0x1C |
| INC H    | 00 100 100 | 0x24 |
| INC L    | 00 101 100 | 0x2C |
| INC (HL) | 00 110 100 | 0x34 |
| INC A    | 00 111 100 | 0x3C |

---

## X=0 and Z=5

Decrement operations in 8 bit registers

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| DEC B    | 00 000 101 | 0x05 |
| DEC C    | 00 001 101 | 0x0D |
| DEC D    | 00 010 101 | 0x15 |
| DEC E    | 00 011 101 | 0x1D |
| DEC H    | 00 100 101 | 0x25 |
| DEC L    | 00 101 101 | 0x2D |
| DEC (HL) | 00 110 101 | 0x35 |
| DEC A    | 00 111 101 | 0x3D |

---

## X=0 and Z=6

Load with immediate bytes

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD B,n    | 00 000 110 | 0x06 |
| LD C,n    | 00 001 110 | 0x0E |
| LD D,n    | 00 010 110 | 0x16 |
| LD E,n    | 00 011 110 | 0x1E |
| LD H,n    | 00 100 110 | 0x26 |
| LD L,n    | 00 101 110 | 0x2E |
| LD (HL),n | 00 110 110 | 0x36 |
| LD A,n    | 00 111 110 | 0x3E |

---

## X=0 and Z=7

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| RLC A    | 00 000 111 | 0x07 |
| RRC A    | 00 001 111 | 0x0F |
| RL A     | 00 010 111 | 0x17 |
| RR A     | 00 011 111 | 0x1F |
| DAA      | 00 100 111 | 0x27 |
| CPL      | 00 101 111 | 0x2F |
| SCF      | 00 110 111 | 0x37 |
| CCF      | 00 111 111 | 0x3F |

---

## X=1 and Y=0

LD B,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD B,B    | 01 000 000 | 0x40 |
| LD B,C    | 01 000 001 | 0x41 |
| LD B,D    | 01 000 010 | 0x42 |
| LD B,E    | 01 000 011 | 0x43 |
| LD B,H    | 01 000 100 | 0x44 |
| LD B,L    | 01 000 101 | 0x45 |
| LD B,(HL) | 01 000 110 | 0x46 |
| LD B,A    | 01 000 111 | 0x47 |

---

## X=1 and Y=1

LD C,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD C,B    | 01 001 000 | 0x48 |
| LD C,C    | 01 001 001 | 0x49 |
| LD C,D    | 01 001 010 | 0x4A |
| LD C,E    | 01 001 011 | 0x4B |
| LD C,H    | 01 001 100 | 0x4C |
| LD C,L    | 01 001 101 | 0x4D |
| LD C,(HL) | 01 001 110 | 0x4E |
| LD C,A    | 01 001 111 | 0x4F |

---

## X=1 and Y=2

LD D,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD D,B    | 01 010 000 | 0x50 |
| LD D,C    | 01 010 001 | 0x51 |
| LD D,D    | 01 010 010 | 0x52 |
| LD D,E    | 01 010 011 | 0x53 |
| LD D,H    | 01 010 100 | 0x54 |
| LD D,L    | 01 010 101 | 0x55 |
| LD D,(HL) | 01 010 110 | 0x56 |
| LD D,A    | 01 010 111 | 0x57 |

---

## X=1 and Y=3

LD E,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD E,B    | 01 011 000 | 0x58 |
| LD E,C    | 01 011 001 | 0x59 |
| LD E,D    | 01 011 010 | 0x5A |
| LD E,E    | 01 011 011 | 0x5B |
| LD E,H    | 01 011 100 | 0x5C |
| LD E,L    | 01 011 101 | 0x5D |
| LD E,(HL) | 01 011 110 | 0x5E |
| LD E,A    | 01 011 111 | 0x5F |

---

## X=1 and Y=4

LD H,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD H,B    | 01 100 000 | 0x60 |
| LD H,C    | 01 100 001 | 0x61 |
| LD H,D    | 01 100 010 | 0x62 |
| LD H,E    | 01 100 011 | 0x63 |
| LD H,H    | 01 100 100 | 0x64 |
| LD H,L    | 01 100 101 | 0x65 |
| LD H,(HL) | 01 100 110 | 0x66 |
| LD H,A    | 01 100 111 | 0x67 |

---

## X=1 and Y=5

LD L,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD L,B    | 01 101 000 | 0x68 |
| LD L,C    | 01 101 001 | 0x69 |
| LD L,D    | 01 101 010 | 0x6A |
| LD L,E    | 01 101 011 | 0x6B |
| LD L,H    | 01 101 100 | 0x6C |
| LD L,L    | 01 101 101 | 0x6D |
| LD L,(HL) | 01 101 110 | 0x6E |
| LD L,A    | 01 101 111 | 0x6F |

---

## X=1 and Y=6

LD (HL),r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD (HL),B | 01 110 000 | 0x70 |
| LD (HL),C | 01 110 001 | 0x71 |
| LD (HL),D | 01 110 010 | 0x72 |
| LD (HL),E | 01 110 011 | 0x73 |
| LD (HL),H | 01 110 100 | 0x74 |
| LD (HL),L | 01 110 101 | 0x75 |
| HALT      | 01 110 110 | 0x76 |
| LD (HL),A | 01 110 111 | 0x77 |

---

## X=1 and Y=7

LD A,r

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| LD A,B    | 01 111 000 | 0x78 |
| LD A,C    | 01 111 001 | 0x79 |
| LD A,D    | 01 111 010 | 0x7A |
| LD A,E    | 01 111 011 | 0x7B |
| LD A,H    | 01 111 100 | 0x7C |
| LD A,L    | 01 111 101 | 0x7D |
| LD A,(HL) | 01 111 110 | 0x7E |
| LD A,A    | 01 111 111 | 0x7F |

---

## X=2 and Y=0

Add

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| ADD A,B    | 10 000 000 | 0x80 |
| ADD A,C    | 10 000 001 | 0x81 |
| ADD A,D    | 10 000 010 | 0x82 |
| ADD A,E    | 10 000 011 | 0x83 |
| ADD A,H    | 10 000 100 | 0x84 |
| ADD A,L    | 10 000 101 | 0x85 |
| ADD A,(HL) | 10 000 110 | 0x86 |
| ADD A,A    | 10 000 111 | 0x87 |

---

## X=2 and Y=1

Add with carry

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| ADC A,B    | 10 001 000 | 0x88 |
| ADC A,C    | 10 001 001 | 0x89 |
| ADC A,D    | 10 001 010 | 0x8A |
| ADC A,E    | 10 001 011 | 0x8B |
| ADC A,H    | 10 001 100 | 0x8C |
| ADC A,L    | 10 001 101 | 0x8D |
| ADC A,(HL) | 10 001 110 | 0x8E |
| ADC A,A    | 10 001 111 | 0x8F |

---

## X=2 and Y=2

Subtract

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| SUB A,B    | 10 010 000 | 0x90 |
| SUB A,C    | 10 010 001 | 0x91 |
| SUB A,D    | 10 010 010 | 0x92 |
| SUB A,E    | 10 010 011 | 0x93 |
| SUB A,H    | 10 010 100 | 0x94 |
| SUB A,L    | 10 010 101 | 0x95 |
| SUB A,(HL) | 10 010 110 | 0x96 |
| SUB A,A    | 10 010 111 | 0x97 |

---

## X=2 and Y=3

Subtract with carry

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| SBC A,B    | 10 011 000 | 0x98 |
| SBC A,C    | 10 011 001 | 0x99 |
| SBC A,D    | 10 011 010 | 0x9A |
| SBC A,E    | 10 011 011 | 0x9B |
| SBC A,H    | 10 011 100 | 0x9C |
| SBC A,L    | 10 011 101 | 0x9D |
| SBC A,(HL) | 10 011 110 | 0x9E |
| SBC A,A    | 10 011 111 | 0x9F |

---

## X=2 and Y=4

Bitwise AND

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| AND A,B    | 10 100 000 | 0xA0 |
| AND A,C    | 10 100 001 | 0xA1 |
| AND A,D    | 10 100 010 | 0xA2 |
| AND A,E    | 10 100 011 | 0xA3 |
| AND A,H    | 10 100 100 | 0xA4 |
| AND A,L    | 10 100 101 | 0xA5 |
| AND A,(HL) | 10 100 110 | 0xA6 |
| AND A,A    | 10 100 111 | 0xA7 |

---

## X=2 and Y=5

Bitwise XOR

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| XOR A,B    | 10 101 000 | 0xA8 |
| XOR A,C    | 10 101 001 | 0xA9 |
| XOR A,D    | 10 101 010 | 0xAA |
| XOR A,E    | 10 101 011 | 0xAB |
| XOR A,H    | 10 101 100 | 0xAC |
| XOR A,L    | 10 101 101 | 0xAD |
| XOR A,(HL) | 10 101 110 | 0xAE |
| XOR A,A    | 10 101 111 | 0xAF |

---

## X=2 and Y=6

Bitwise OR

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| OR A,B    | 10 110 000 | 0xB0 |
| OR A,C    | 10 110 001 | 0xB1 |
| OR A,D    | 10 110 010 | 0xB2 |
| OR A,E    | 10 110 011 | 0xB3 |
| OR A,H    | 10 110 100 | 0xB4 |
| OR A,L    | 10 110 101 | 0xB5 |
| OR A,(HL) | 10 110 110 | 0xB6 |
| OR A,A    | 10 110 111 | 0xB7 |

---

## X=2 and Y=7

Compare

| Mmemonic  |   x y z    | Hex  |
| :-------- | :--------: | :--: |
| CP A,B    | 10 111 000 | 0xB8 |
| CP A,C    | 10 111 001 | 0xB9 |
| CP A,D    | 10 111 010 | 0xBA |
| CP A,E    | 10 111 011 | 0xBB |
| CP A,H    | 10 111 100 | 0xBC |
| CP A,L    | 10 111 101 | 0xBD |
| CP A,(HL) | 10 111 110 | 0xBE |
| CP A,A    | 10 111 111 | 0xBF |

---

## X=3 and Z=0

Relative returns, I/O loads and stack manipulation

| Mmemonic      |   x y z    | Hex  |
| :------------ | :--------: | :--: |
| RET NZ        | 11 000 000 | 0xC0 |
| RET Z         | 11 001 000 | 0xC8 |
| RET NC        | 11 010 000 | 0xD0 |
| RET C         | 11 011 000 | 0xD8 |
| LD (FF00+n),A | 11 100 000 | 0xE0 |
| ADD SP,d      | 11 101 000 | 0xE8 |
| LD A,(FF00+n) | 11 110 000 | 0xF0 |
| LDHL SP,d     | 11 111 000 | 0xF8 |

---

## X=3 and Z=1

Stack pop and absolute returns

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| POP BC   | 11 000 001 | 0xC1 |
| RET      | 11 001 001 | 0xC9 |
| POP DE   | 11 010 001 | 0xD1 |
| RETI     | 11 011 001 | 0xD9 |
| POP HL   | 11 100 001 | 0xE1 |
| JP (HL)  | 11 101 001 | 0xE9 |
| POP AF   | 11 110 001 | 0xF1 |
| LD SP,HL | 11 111 001 | 0xF9 |

---

## X=3 and Z=2

Absolute conditional jumps, I/O load

| Mmemonic      |   x y z    | Hex  |
| :------------ | :--------: | :--: |
| JP NZ,nn      | 11 000 010 | 0xC2 |
| JP Z,nn       | 11 001 010 | 0xCA |
| JP NC,nn      | 11 010 010 | 0xD2 |
| JP C,nn       | 11 011 010 | 0xDA |
| LD (FF00+C),A | 11 100 010 | 0xE2 |
| LD (nn),A     | 11 101 010 | 0xEA |
| LD A,(FF00+C) | 11 110 010 | 0xF2 |
| LD A,(nn)     | 11 111 010 | 0xFA |

---

## X=3 and Z=3

Absolute jump, prefix and interrupts

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| JP nn    | 11 000 011 | 0xC3 |
| PREFIX   | 11 001 011 | 0xCB |
| XXXX     | 11 010 011 | 0xD3 |
| XXXX     | 11 011 011 | 0xDB |
| XXXX     | 11 100 011 | 0xE3 |
| XXXX     | 11 101 011 | 0xEB |
| DI       | 11 110 011 | 0xF3 |
| EI       | 11 111 011 | 0xFB |

---

## X=3 and Z=4

Conditional calls

| Mmemonic   |   x y z    | Hex  |
| :--------- | :--------: | :--: |
| CALL NZ,nn | 11 000 100 | 0xC4 |
| CALL Z,nn  | 11 001 100 | 0xCC |
| CALL NC,nn | 11 010 100 | 0xD4 |
| CALL C,nn  | 11 011 100 | 0xDC |
| XXXX       | 11 100 100 | 0xE4 |
| XXXX       | 11 101 100 | 0xEC |
| XXXX       | 11 110 100 | 0xF4 |
| XXXX       | 11 111 100 | 0xFC |

---

## X=3 and Z=5

Stack push

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| PUSH BC  | 11 000 101 | 0xC5 |
| CALL nn  | 11 001 101 | 0xCD |
| PUSH DE  | 11 010 101 | 0xD5 |
| XXXX     | 11 011 101 | 0xDD |
| PUSH HL  | 11 100 101 | 0xE5 |
| XXXX     | 11 101 101 | 0xED |
| PUSH AF  | 11 110 101 | 0xF5 |
| XXXX     | 11 111 101 | 0xFD |

---

## X=3 and Z=6

8 bit ALU with immediate byte

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| ADD A,n  | 11 000 110 | 0xC6 |
| ADC A,n  | 11 001 110 | 0xCE |
| SUB A,n  | 11 010 110 | 0xD6 |
| SBC A,n  | 11 011 110 | 0xDE |
| AND A,n  | 11 100 110 | 0xE6 |
| XOR A,n  | 11 101 110 | 0xEE |
| OR A,n   | 11 110 110 | 0xF6 |
| CP A,n   | 11 111 110 | 0xFE |

---

## X=3 and Z=7

Reset table

| Mmemonic |   x y z    | Hex  |
| :------- | :--------: | :--: |
| RST 0    | 11 000 111 | 0xC7 |
| RST 8    | 11 001 111 | 0xCF |
| RST 10   | 11 010 111 | 0xD7 |
| RST 18   | 11 011 111 | 0xDF |
| RST 20   | 11 100 111 | 0xE7 |
| RST 28   | 11 101 111 | 0xEF |
| RST 30   | 11 110 111 | 0xF7 |
| RST 38   | 11 111 111 | 0xFF |
