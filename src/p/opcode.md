## Opcode Reference

Here is all the instructions that you may need to program the CPU.

**rr**  16-bits register
**r**   8-bits registers
**nn**  16-bits constant
**n**   8-bits constant
**p**   Pointer

### halt

Stops the system and turns it off.

    Instr.  Args        Opcode
    HALT                0x00

### nop

Does nothing.

    Instr.  Args        Opcode
    NOP                 0x01

## Stack manipulation

These instructions can be used to manipulate the stack by pushing and popping
values from it.

### push rr

Pushes the specified 16-bit register.

    Instr.  Args        Opcode
    PUSH    HL          0x02
    PUSH    BC          0x03
    PUSH    DE          0x04

### pusha

Pushes all the 16-bit registers in the following order :

 - HL
 - BC
 - DE

.

    Instr.  Args        Opcode
    PUSHA               0x05
    
### pop rr

Pops stack into the specified 16-bit register.

    Instr.  Args        Opcode
    POP     HL          0x06
    POP     BC          0x07
    POP     DE          0x08

### popa

Pops stack into all the 16-bit registers in the following order: 

 - DE
 - BC
 - HL

.

    Instr.  Args        Opcode
    POPA                0x09

## mov Instructions

Moves a value to a register or memory address.

### mov r1, r2

Moves r2 to r1.

    Instr.  Args        Opcode
    mov     A, A        0x0a
    mov     A, B        0x0b
    mov     A, C        0x0c
    mov     A, D        0x0d
    mov     A, E        0x0e
    mov     A, H        0x0f
    mov     A, L        0x10
    
    mov     B, A        0x11
    mov     B, B        0x12
    mov     B, C        0x13
    mov     B, D        0x14
    mov     B, E        0x15
    mov     B, H        0x16
    mov     B, L        0x17
    
    mov     C, A        0x18
    mov     C, B        0x19
    mov     C, C        0x1a
    mov     C, D        0x1b
    mov     C, E        0x1c
    mov     C, H        0x1d
    mov     C, L        0x1e
    
    mov     D, A        0x1f
    mov     D, B        0x20
    mov     D, C        0x21
    mov     D, D        0x22
    mov     D, E        0x23
    mov     D, H        0x24
    mov     D, L        0x25
    
    mov     E, A        0x26
    mov     E, B        0x27
    mov     E, C        0x28
    mov     E, D        0x29
    mov     E, E        0x2a
    mov     E, H        0x2b
    mov     E, L        0x2c
    
    mov     H, A        0x2d
    mov     H, B        0x2e
    mov     H, C        0x2f
    mov     H, D        0x30
    mov     H, E        0x31
    mov     H, H        0x32
    mov     H, L        0x33
    
    mov     L, A        0x34
    mov     L, B        0x35
    mov     L, C        0x36
    mov     L, D        0x37
    mov     L, E        0x38
    mov     L, H        0x39
    mov     L, L        0x3a

### mov (HL), r

Moves r to (HL).

    Inst.   Args        Opcodes
    mov     (HL), A     0x3b
    mov     (HL), B     0x3c
    mov     (HL), C     0x3d
    mov     (HL), D     0x3e
    mov     (HL), E     0x3f
    mov     (HL), H     0x40
    mov     (HL), L     0x41

### mov r, n

Moves n to r.

    Inst.   Args        Opcodes
    mov     A, n        0x42
    mov     B, n        0x43
    mov     C, n        0x44
    mov     D, n        0x45
    mov     E, n        0x46
    mov     H, n        0x47
    mov     L, n        0x48

### mov (HL), n

Moves n to (HL).

    Inst.   Args        Opcodes
    mov     (HL), n     0x49

### mov r, (HL)

Moves (HL) to r.

    Inst.   Args        Opcodes
    mov     A, (HL)     0x4a
    mov     B, (HL)     0x4b
    mov     C, (HL)     0x4c
    mov     D, (HL)     0x4d
    mov     E, (HL)     0x4e
    mov     H, (HL)     0x4f
    mov     L, (HL)     0x50
    
### mov SP, nn

Sets the stack pointer to nn.

    Inst.   Args        Opcodes
    mov     SP, nn      0x51
    
### mov A, (BC/DE)

Moves (BC/DE) to A.

    Inst.   Args        Opcodes
    mov     A, (BC)     0x52
    mov     A, (DE)     0x53

### mov A, (nn)

Moves (nn) to A.

    Inst.   Args        Opcodes
    mov     A, (nn)     0x54

### mov (BC/DE), A

Moves A to (BC/DE)

    Inst.   Args        Opcodes
    mov     (BC), A     0x55
    mov     (DE), A     0x56

### mov (nn), A

Moves A to (nn)

    Inst.   Args        Opcodes
    mov     (nn), A     0x57

### mov rr, nn

Moves nn to a 16-bit register.

    Inst.   Args        Opcodes
    mov     HL, nn      0x58
    mov     BC, nn      0x59
    mov     DE, nn      0x5a

## Arithmetic

These are the arithmetic instructions. It operates on the `A` register.

Example :

    add B       ; A = A + B
    xor (HL)    ; A = A ^ (HL)

### add r

Adds the value of r to A.

    Inst.   Args        Opcodes
    add     A           0x5b
    add     B           0x5c
    add     C           0x5d
    add     D           0x5e
    add     E           0x5f
    add     H           0x60
    add     L           0x61

### add n

Adds n to A.

    Inst.   Args        Opcodes
    add     n           0x62

### add (HL)

Adds (HL) to A.

    Inst.   Args        Opcodes
    add     (HL)        0x63
    
### sub r

Substracts the value of r to A.

    Inst.   Args        Opcodes
    sub     A           0x64
    sub     B           0x65
    sub     C           0x66
    sub     D           0x67
    sub     E           0x68
    sub     H           0x69
    sub     L           0x6a
    
### sub n

Subtracts n to A.

    Inst.   Args        Opcodes
    sub     n           0x6b

### sub (HL)

Substracts (HL) to A.

    Inst.   Args        Opcodes
    sub     (HL)        0x6c
    
### and r

Does a bitwise AND operation with A and the value of r.

    Inst.   Args        Opcodes
    and     A           0x6d
    and     B           0x6e
    and     C           0x6f
    and     D           0x70
    and     E           0x71
    and     H           0x72
    and     L           0x73

### and n

Does a bitwise AND operation with A and n.

    Inst.   Args        Opcodes
    and     n           0x74

### and (HL)

Does a bitwise AND operation with A and (HL).

    Inst.   Args        Opcodes
    and     (HL)        0x75

### or r

Does a bitwise OR operation with A and the value of r.

    Inst.   Args        Opcodes
    or      A           0x76
    or      B           0x77
    or      C           0x78
    or      D           0x79
    or      E           0x7a
    or      H           0x7b
    or      L           0x7c

### or n

Does a bitwise OR operation with A and n.

    Inst.   Args        Opcodes
    or      n           0x7d

### or (HL)

Does a bitwise OR operation with A and (HL).

    Inst.   Args        Opcodes
    or      (HL)        0x7e

### xor r

Does a bitwise XOR operation with A and the value of r.

    Inst.   Args        Opcodes
    xor     A           0x7f
    xor     B           0x80
    xor     C           0x81
    xor     D           0x82
    xor     E           0x83
    xor     H           0x84
    xor     L           0x85

### xor n

Does a bitwise XOR operation with A and n.

    Inst.   Args        Opcodes
    xor     n           0x86

### xor (HL)

Does a bitwise XOR operation with A and (HL).

    Inst.   Args        Opcodes
    xor     (HL)        0x87

## Increment and Shift

These arithmetic instructions are different because the result will not affect
the A register but the specified register itself

### inc r

Increments r.

    Inst.   Args        Opcodes
    inc     A           0x88
    inc     B           0x89
    inc     C           0x8a
    inc     D           0x8b
    inc     E           0x8c
    inc     H           0x8d
    inc     L           0x8e

### inc rr

Increments rr.

    Inst.   Args        Opcodes
    inc     HL          0x8f
    inc     BC          0x90
    inc     DE          0x91

### dec r

Decrements r.

    Inst.   Args        Opcodes
    dec     A           0x92
    dec     B           0x93
    dec     C           0x94
    dec     D           0x95
    dec     E           0x96
    dec     H           0x97
    dec     L           0x98

### dec rr

Decrements rr.

    Inst.   Args        Opcodes
    dec     HL          0x99
    dec     BC          0x9a
    dec     DE          0x9b

### sl r

Bitwise shift r to left.

    Inst.   Args        Opcodes
    sl      A           0x9c
    sl      B           0x9d
    sl      C           0x9e
    sl      D           0x9f
    sl      E           0xa0
    sl      H           0xa1
    sl      L           0xa2

### sr r

Bitwise shift r to right.

    Inst.   Args        Opcodes
    sr      A           0xa3
    sr      B           0xa4
    sr      C           0xa5
    sr      D           0xa6
    sr      E           0xa7
    sr      H           0xa8
    sr      L           0xa9

## Conditions and jumps

The following instructions will be about executing conditions and jumping
through the code.

Conditions works like this :

 - Compare A with x
 - If A == x set Zero Flag to 1
 - Else set Zero Flag to 0
 - If A < x then set Carry Flag to 1
 - Else set Carry Flag to 0

### cp r

Compare A with r.

    Inst.   Args        Opcodes
    cp      A           0xaa
    cp      B           0xab
    cp      C           0xac
    cp      D           0xad
    cp      E           0xae
    cp      H           0xaf
    cp      L           0xb0

### cp n

Compare A with n.

    Inst.   Args        Opcodes
    cp      n           0xb1

### cp (HL)

Compare A with (HL).

    Inst.   Args        Opcodes
    cp      (HL)        0xb2

### jp nn

Jumps at nn.

    Inst.   Args        Opcodes
    jp      nn          0xb3

### jp HL

Jumps at HL.

    Inst.   Args        Opcodes
    jp      (HL)        0xb4

### jc nn

Jumps at nn if Carry Flag is on.

    Inst.   Args        Opcodes
    jc      nn          0xb5

### jc (HL)

Jumps at (HL) if Carry Flag is on.

    Inst.   Args        Opcodes
    jc      (HL)        0xb6

### jz nn

Jumps at nn if Zero Flag is on.

    Inst.   Args        Opcodes
    jz      nn          0xb7

### jz (HL)

Jumps at (HL) if Zero Flag is on

    Inst.   Args        Opcodes
    jz      (HL)        0xb8

### jn nn

Jumps at nn if Zero Flag is off.

    Inst.   Args        Opcodes
    jn      nn          0xb9

### jn (HL)

Jumps at (HL) if Zero Flag is off.

    Inst.   Args        Opcodes
    jn      (HL)        0xba
    
### call nn

Push the Program Counter into the stack and jumps at nn.

    Inst.   Args        Opcodes
    call    nn          0xbb

### call (HL)

Push the Program Counter into the stack and jumps at (HL).

    Inst.   Args        Opcodes
    call    (HL)        0xbc

### ret

Pops the stack into the Program Counter.

    Inst.   Args        Opcodes
    ret                 0xbd
    
## Dumping instructions

These are two instructions designed to debug the program.

### dumpr

Dumps all the registers.

    Inst.   Args        Opcodes
    dumpr               0xbe

### dumpm nn

Dumps the memory from (nn) to (nn+0xf)

    Inst.   Args        Opcodes
    dumpm   nn          0xbf

## Misc.

### slp

Sleeps for 30000 microseconds to avoid 100% CPU usage on the host machine.

    Inst.   Args        Opcodes
    slp                 0xc0
    
[Go back to the CPU manual](cpu.html)
