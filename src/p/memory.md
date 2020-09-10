## Memory properties and bindings

### Table of contents

 - Properties
 - Bindigs/Mappings
 
### Properties

The memory is nothing special, just 64 KiB of addressable memory. Which 32 KiB
are reserved for the ROM, 4 KiB for the GPU and 16 bytes for the I/O.

### Bindings/Mappings

Here are the binding table of the memory.

    +-----------+------------+
    | 0000-7FFF | ROM        |
    |  32  KiB  | allocation |
    +-----------+------------+
    | 8000-8FFF | VRAM       |
    |   4  KiB  |            |
    +-----------+------------+
    | 9000-FFEF | General P. |
    |  ~28 KiB  | RAM        |
    +-----------+------------+
    | FFEF-FFFF | I/O Binds  |
    +-----------+------------+

More details about the VRAM and the I/O Binds will be given in the appropriate
pages.

[Next: CPU prorgamming reference](cpu.html)
