# VICasm Documentation

## Pseudo-instructions

Pseudo-instructions are instructions that aren't assembled to be run by the
CPU but most likely instructions to indicate the assembler to perform a
specific operation such as including another assembly file or adding directly
binary content.

### Pseudo-instruction set

`.define NAME VALUE` defines the constant NAME to VALUE.

Example :

    .define TEST 34     ; Sets TEST to 34
    .define TSET TEST   ; Any constants works
    
    mov a,  TEST        ; sets a to TEST
    mov b,  TSET        ; sets b to TSET
    dumpr               ; Verifying using dumpr

`.include "FILENAME"` includes an assembly file.

**NOTE** FILENAME must be specified in the command-line arguments.

`.bin "FILENAME"` appends a raw binary file to the output file.

`.db VALUE, VALUE, ...` appends raw binary to the output file.

`NAME:` defines the constant NAME to the current location.
