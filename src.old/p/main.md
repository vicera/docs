## Main usage

### Table of contents

 - Quick explaination
 - Command-line arguments

### Quick explaination

The VICERA is a 8-bit fantasy console inspired by the Nintendo Gameboy.  
It features a CPU close to the Gameboy Z80-like architecture, 7 general purpose
registers, a monochrome 160x160 display and tile and sprite support of the GPU.

This page is about how to use the console for gaming or testing purposes.

### Command-line arguments

The system doesn't contain any GUI front-end to manage or configure it. You do
everything from the command-line using arguments and a configuration file.

There are only a very few flags so this page won't be long. 

    -r, --rom <ROMFILE>

This flag is essential, it specifies the ROM to be run by the system. Without it
you can't run it.

    -s, --start-at <ADDRESS>

This flag can be used for development purposes, it allows you to start the
progra, at the specified address between 0x0000 and 0xffff. The address must
be written in hexadecimal.

    -c, --config <CONFIG>

Loads a configuration file. To look up how to roll your own configuration,
please refer to [Configuration](config.html)

    -v, --version

Prints the version of the build then exit.

    -h, --help

Displays usage then exit.

[Next: Configuration](config.html)
