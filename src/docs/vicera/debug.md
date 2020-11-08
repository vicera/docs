# VICERA Documentation

## Debugger

The debugging features in the VICERA allows you to dump memory, registers and
even disassembled code. There are instructions and command-line arguments
specially designed for these.

### Command-line arguments

There are 3 command-lines arguments that may be used to debug your program,

`-D` or `--disasm` which doesn't run the VICERA but gives you a full disassembly
of the specified ROM instead.

`-j` or `--debug-on-jump` which disassembles the 5 next instructions after a
jump.
This feature may be useful if your program doesn't jump where it is intended
to.

`-d` or `--debug` which disassembles every single instruction the CPU runs.
This will however extremely slow down the console. I don't recommend using this
but using the `dbg` instruction instead.

### Instruction

The VICERA provides 3 instructions to deal with debugging. `dbg`, `dumpm` and
`dumpr`.

`dbg` disassembles the 5 next instructions and outputs them in the logs.
`dumpm` dumps the 16 next bytes of a specified location in the memory.
`dumpr` dumps all the registers.

### Debug logs

The debug logs should look like this

    [#] |debug.c| #0069	MOV	A, 	(#fff2)
    [#] |debug.c| #006b	CP	#00
    [#] |debug.c| #006e	JZ	#0083
    [#] |debug.c| #0071	JP	#007b
    [#] |debug.c| #0074	MOV	A, 	(#fff0)
    [#] |debug.c| #0076	CP	#80
    [#] |debug.c| #0079	JN	#0083
    [#] |debug.c| #007a	HALT	 
    [#] |debug.c| #007c	SUB	A, 	#02
    [#] |debug.c| #007f	MOV	(#fff2),A
    [#] |debug.c| #0082	JP	#0083
    [#] |debug.c| #0083	POPA	 
    [#] |debug.c| #0084	RET	 
    [#] |debug.c| #0087	MOV	SP, 	#ffef
    [#] |debug.c| #008a	CALL	#0033
    [#] |debug.c| #008d	CALL	#0053
    [#] |debug.c| #0090	DUMPM	#8738
    [#] |debug.c| #0092	MOV	A, 	#80
    [#] |debug.c| #0095	MOV	(#fff2),A
    [#] |debug.c| #0098	MOV	A, 	(#fff0)
    [#] |debug.c| #0099	MOV	B, 	A
    [#] |debug.c| #009c	MOV	A, 	(#fff0)

It specifies the location in the memory, then the instruction and finally it's
arguments. All values are using the hexadecimal notation and the instructions
are written in a sort of Intel syntax.
