## Controller

The controller is made of a directional cross, a Select, Start, A
and B buttons. Everything is stored in FFF4, each bit represents
a button and is set to 1 if pressed, and 0 if not.

    Controller bindings at FFF4
    
    0 0 0 0 0 0 0 0
    | | | | | | | |
    | | | | | | | B
    | | | | | | A
    | | | | | Select
    | | | | Start
    | | | Left
    | | Down
    | Right
    Up