# VICasm Documentation

## General syntax

The assembler uses a sort of Intel syntax like specified in the introduction.
It goes as it follows

    ; This is a comment
    Label:          ; Label
    mov a,  b       ; A = B, the destination first then the source
    
    1234            ; Decimal number
    0x1234          ; Hexadecimal number
    033             ; Octal number
    (0xcafe)        ; Pointer at the address
    (HL)            ; Registers can also be used as pointers
    
    AdD A, 0xfe     ; Instructions aren't case-sensitive
    jp Label        ; However labels are
    
    mov hl, Label   ; Labels can also be used as constants
    
    .define TEST 1  ; Pesudo-instructions start with a dot
    cp  TEST        ; Definitions can also be used as constants
    
## Command-line arguments

The VICasm has only one argument: `-o FILE` which outputs the assembled file at
FILE instead of `a.out`. All the assembly files must be specified in the
assembler. The main one must be specified before the other ones.

For example, if I want to make a binary named `game.rom` with 3 files assembly
files named respectively `main.s level1.s math.s`, I must execute vicasm like
this in my shell:

    $ # Assemble the files
    $ vicasm -o game.rom main.s level.s math.s
    Adding level.s...
    Adding math.s...
    $ # Making sure it's there
    $ ls game.rom
    game.rom
    

