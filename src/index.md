# The VICERA Project

Welcome to the official website of the VICERA project!

The VICERA project is a project that aims to create a fantasy console with a
CPU close to what you could get in 80s micro-computers. In fact, the VIC-8P,
the CPU that powers the fantasy console is heavily inspired by the Zilog Z80.

This project comes with software to play and create games for it.

## [VICERA](https://github.com/vicera/vicera)

This is the fantasy console itself, including the CPU, the GPU and a front-end
to play games. Unfortunately, the front-end only works on Linux for now because
I don't have a Windows computer to work on and the Windows C API seems to suck.

There are possibilities that I work on a Windows front-end in the future but
don't expect much from it.

It features 64 KiB of RAM, an 8-bit CPU with 16-bit addressing, a 160x160
monochrome screen which works with tiles and sprites.

## [VICasm](https://github.com/vicera/vicasm)

This software is the assembler for the VIC-8P CPU. It features labels, constant
definitions and multiple assembly files support.

## [VICERA Collection](https://git.h3liu.ml/vcollection)

This is a personal collection of software that I have wrote as a side project
made with components of VICERA project. Such as a snake written in assembly or
a brainfuck interpreter.

## [Documentation](/vicera/docs)

You might need it if you are programming it unless you like reading C and C++
code.
