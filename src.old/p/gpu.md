## GPU Reference

The GPU is a crucial feature, it generates the graphics to display on the
screen. The VICERA GPU works with tiles and sprites and it can contain up to
64 sprites and 256 tiles in the VRAM. It uses the memory from 0x8000 to 0x8fff

### Table of Contents

 - Quick overview
 - Memory bindings
 - Tiles and Sprites format
 - Tiles indexing
 - Sprites indexing
 - Scrolling and Refreshing

### Quick overview

The GPU is the component of the VICERA that is required to process graphics,
tiles and sprites. It can only handle 1-bit displays (monochrome), can support
up to 64 sprites on the screen at once and store up to 64 sprites and 256
tiles. It uses 4 KiB of the memory from 0x8000 to 0x8FFF.

The GPU also has a few I/O Bindings from 0xfff0 to 0xfff2, one for refreshing and 2 for scrolling.

**NOTE** The system display is of 160x160 but the actual rendered screen size
is 256x256 pixels. Only 160x160 are visible. However, the zone that has to be
displayed can be moved by modifying 2 variables in the memory.

### Memory bindings

The VRAM is divided into 4 parts :
 - The sprites index
 - The tiles index
 - The sprite memory
 - The tiles memory

And contains a few I/O Binds as mentionned before.

Here is a little scheme :

    +---------------+-----------+------+
    | Sprites index | 8000-80FF |      |
    |  Tiles index  | 8100-84FF |      |
    | Sprites  mem. | 8500-86FF | VRAM |
    |  Tiles  mem.  | 8700-8EFF |      |
    +---------------+-----------+------+
    |    Refresh    |   FFF0    |      |
    |    SCROLLX    |   FFF1    |  I/O |
    |    SCROLLY    |   FFF2    |      |
    +---------------+-----------+------+

The memory will contains the sprite itself when the indexing
will just be there to know what to place on the screen.

### Tiles and sprites format

Since the GPU only supports 1-bit graphics, Storing one sprite or tile requires
only 8 bytes of memory. These are just 8x8 bitmaps stored in binary format like
this :

    ; Example of sprite
    Sprite:
        db 0b11111111   ; ########
        db 0b10000001   ; #      #
        db 0b10000001   ; #      #
        db 0b10000001   ; #      #
        db 0b10000001   ; #      #
        db 0b10000001   ; #      #
        db 0b10000001   ; #      #
        db 0b11111111   ; ########

The bitmap above is supposed to display a square. This sprite will then have to
be moved in some area in the sprite or tile memory.

### Tiles indexing

Indexing tiles is really simple. The tile index is of 1 KiB which each byte 
matches one spot to be rendered on the screen. Since the tiles memory can contain up to 256 tiles, each byte will contain the index of the required tile.

The screen (not the visible area, the whole screen) can support up to 64x64
tiles to be displayed at once.

To calculate memory location of a specific index, you can just do
`0x8100 + (8 * index)`.

To calculate the X and Y position of a tile to place it in the index, you can
also do `0x8100 + (x + (y * 64))`

### Sprites indexing

Sprite indexing is a little bit more complex since the visibility and the
position also has to be specified. One sprite can go wherever it wants to,
unlike a tile. However, the sprite memory works just like the tile memory.

The screen can only contain 64 sprites at once.

Each "indexing cell" contains 4 bytes of information :

    A sprite "indexing cell"

    01 04 de ad
    |  |  |  |
    |  |  |  Y Position of the sprite
    |  |  X Position of the sprite
    |  ID of the sprite stored in the Sprites memory
    (Boolean) is it active?

**The first byte** tells if the sprite has to be displayed or not.
**The second byte** specifies the index of the sprite between 0 and 63.
**The last bytes** specifies the X and Y position of the sprite.

### Scrolling and refreshing

As mentionned before, the GPU uses 3 bytes of the reserved I/O
memory location. One for screen refreshing, two for scrolling.

**FFF0** will increment everytime the screen refreshes, allowing
the programmer to know when it refreshes from the CPU.

    ; This is an example of game loop
    jp Main
    
    MainLoop:                   ; Game loop routine
        ret
    
    Main:
        Main_L:
            mov A, (0xfff0)     ; reads at fff0
            mov B, A            ; keep the result in B
            WaitScr:
                mov A, (0xfff0) ; reads at fff0 again
                cp B            ; compare A and B
                slp             ; microsleep
                jz WaitScr      ; continue loop if A == B
            
            call MainLoop       ; else call the main loop
            jp Main_L           ; continue for the next ref.

**FFF1-FFF2** are the scrolling variables to specify where to display. **FFF1** is the X offset and **FFF2** the Y offset.

For example, if both values are set to 0, it will display from
0x0 to 160x160. If the values are set to 254, it will display
from 254x254 to 158x158.

[Next: Controller](controller.html)