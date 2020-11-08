# VICERA Documentation

## CPU programming reference

The CPU architecture is pretty simple and is more or less inspired by the
Gameboy Z80-like CPU. It contains 7 registers and some basic opcodes.

### Table of Contents

 - Quick overview
 - Registers
 - Memory addressing rules
 - Opcode reference

### Quick overview

The VICERA CPU (named VIC-8P) is the CPU used in the console. It has 7 general
purpose registers like said in the introduction, which 2 can be used to point
at some location in memory, a program counter and a stack pointer. It supports 
only 16-bit addressing so the maximum of supported RAM is 64 KiB.

The CPU has basic instructions such as

    mov     add     sub     push    pusha   pop     popa
    halt    nop     and     or      xor     inc     dec
    sl      sr      cp      jp      jc      jz      jn
    call    ret     dumpr   dumpm   slp     dbg

The list above is the complete list of instructions that can be used to program
the CPU. A complete reference of all of those will be written in the last
chapter of this page.

The CPU also contains two flags that may be used to do conditional jumps. This
can't be directly accessed however.

The flags are the first two bits of an 8-bit value stored in it.

    FLAGS IN THE CPU
    
    0 0 0 0 0 0 0 0
                | |
                | Zero flag
                Carry flag

The flags are updated when a condition is tested or if an arithmetic operation
has been done. For example, if the result of the operation is 0, the zero flag
will be set, else it is reset. If the result of the operation does an integer
overflow, the carry flag will be set.

### Registers

As mentionned twice before, the CPU has 7 general purpose registers. Including
1 for arithmetics and 2 to point addresses. It also contains a stack pointer.

    Registers
    ---------
    
    A - Accumulator
    B
    C
    D
    E
    H - Higher value of address pointer
    L - Lower value of address pointer

The `A` register will contain the result of operations such as `add`, `sub`,
`and`, etc.  
The H and L registers will most likely be used to point addresses.

    ; Example use of the H and L registers
    
    mov HL, 0x1234  ; H, L = 0x12, 0x34
    mov A, 0x42     ; A = 0x42
    mov (HL), A     ; (HL) = A -> writes 0x42 at the 0x1234 address

BC and DE can also be used to store 16-bit values and can also be pushed and
popped from the stack like HL

### Memory addressing rules

I'd like to mention that you can't modify and point the memory from any
registers.

Here are the memory addressing rules :

 - Only the content of the `A` register can be moved into memory addresses specified by BC and DE or directly.
 - Same but reversed. The pointed value specified by BC, DE or a constant 16-bits value can only be moved to A.
 - Any registers, however can access the memory pointed at HL.

I don't know if it's precise because I am not really good at explaining but I
hope you will figure it out or you have understood.

### Opcode reference

[Refer to this page](opcode.html)

## Developer's note

You can use `cpu.c`, `logging.c`, `logging.h` and `cpu.h` individually since it
doesn't depend on anything in the VICERA. Then, with these you can implement
your own machine based on the CPU!  
[Here is a good example](https://git.h3liu.ml/vcollection/vic8p-brainfuck)

Modifying the CPU should also not be difficult since it is just a long
switch-case statement and a bunch of small functions.
