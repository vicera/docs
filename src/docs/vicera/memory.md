# VICERA Documentation

## Memory

This system doesn't have any MMU. Everything is stored in 64 kilobytes of RAM
with a standardized structure.

### Scheme

Here is a little ASCII table showing the structure

    MEMORY STRUCTURE STANDARD FOR THE VICERA
    
    0x0000 +-----------+----------------------+
    ...    |    ROM    |  32kb of ROM space   |
    0x8000 +-----------+----------------------+
    ...    |   VRAM    |   RAM for the GPU    |
    0x9000 +-----------+----------------------+
    ...    |   GPRAM   | General Purpose RAM  |
    0xfff0 +-----------+----------------------+
    ...    |    I/O    | I/O Memory registers |
    0xffff +-----------+----------------------+

### ROM

The ROM section is from 0x0000 to 0x7fff and is where the ROM content is copied
to be executed. The execute starts at 0x0000.

It is not recommended that the ROM is bigger than 32 KiB because it may write
in other parts of the memory.

### VRAM

This is the part of the RAM used for the GPU. It contains all the data for the
sprites and the tiles. You can learn more about it by visiting the
[chapter about the GPU](gpu.html).

### General purpose RAM

Do whatever you want with it.

### I/O Registers

This part of the RAM contains all the I/O Memory-mapped registers like the
screen refresh or the controller input.

    ADDRESS     DESCRIPTION     COMPONENT
    --------------------------------------
    0xfff0      Screen refresh  GPU
    0xfff1      Scrolling X     GPU
    0xfff2      Scrolling Y     GPU
    0xfff3      Input           Controller
    
