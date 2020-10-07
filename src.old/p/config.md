## Configuration

This page will explain everything about how to write your own configuration
file to personalize your gaming experience.

### Table of contents

 - Layout of a configuration file
 - Available options

### Layout of a configuration file

The layout is really simple. It has been designed to be easy to use (and also
easy to parse in C).

    key = value
    # This is a comment

Any invalid key or syntax will be ignored by the parser.

### Available options

There are only a few options available to configurate because there isn't
much that is needed. And everything is related to keyboard mappings of the
controller.

All the mappings must be SDL keycodes (unless you have modified the front-end
to use something else than SDL). You can find one [here](https://wiki.libsdl.org/SDLKeycodeLookup).  
You will need to provide the decimal value

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

[Next: Memory properties and bindings](memory.html)    
