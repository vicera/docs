# VICERA Documentation

## Front-end

_**DEVELOPER NOTE:** This chapter concerns `main.c` and `config.c`._

The front-end is an essential part of the VICERA because it puts all the pieces
together to make the VICERA work. The current front-end only works for POSIX
Systems (Linux, BSD, Mac OS X, etc..) due to the use of POSIX libraries. I will
make a Windows front-end Someday:tm:.

### Command-line arguments.

The front-end doesn't have a GUI. You run it using command-line. Why? Because
I don't like GUIs. This chapter covers all the arguments and flags that you can
use.

`-r FILE`, `--rom FILE` sets the rom file to run.
**This argument is required or else the VICERA will refuse to run.**

`-s ADDR`, `--start-at ADDR` starts the VICERA at a specific address in the RAM.
(in hexadecimal)

`-c CONFIG`, `--config CONFIG` loads a config file. Config files are used to
set up the controller keys and sockets.

`-j`, `--debug-on-jump` will disassemble the 5 next instructions after a jump
opcode (`jp`, `jc`, `call`, etc.).

`-d`, `--debug` disassembles every single instruction ran by the CPU.
**Use it only for development purposes, using this will cause severe slowdown.**

`-v`, `--version` displays the version then exit.

`-h`, `--help` displays help then exit.

There will have the socket arguments and flags once I have developed it. The
socket extension hasn't been developed yet.

### Configuration

The configuration is a simplified version of INI (because I hate parsing stuff
in C). You can comment with `#` and every invalid line will be skipped.

The only point of this configuration file is to map the controller to the
keyboard. The keycodes are integer according to the SDL keycodes.
Here is a [reference of keycodes](https://wiki.libsdl.org/SDLKeycodeLookup).

**NOTE** The documentation assumes you are using the official implementation of
the front-end which uses SDL.

Here is the default configuration. All the keycodes are written as decimal
integers.

    # This is the default configuration    
    # Directional arrows -> Keyboard arrows    
    # A, B               -> Z, X    
    # Start, Select      -> Enter, Backspace    
                        
    # Directional arrows    
    controller.left     = 1073741903    
    controller.down     = 1073741905    
    controller.right    = 1073741904    
    controller.up       = 1073741906    
                        
    # Buttons           
    controller.a        = 122    
    controller.b        = 120    
    controller.start    = 13    
    controller.select   = 8 
    
### Developer's Notes

The front-end is nothing more than `main.c` and `sdl_gpu.c`, you can rewrite
these however you want to make your own front-end. A basic front-end should be
able to transfer a ROM into the CPU memory and run both CPU and GPU. The
official front-end uses threading to run CPU and GPU at the same time.
