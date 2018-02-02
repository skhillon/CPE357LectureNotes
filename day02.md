# Day 2
Taylor CPE 357
Wednesday, Jan 10, 2018

- C virtual address space has a global and static area. 
- Stack goes one way, heap goes the other way.
- Your data can be in 3 spaces in memory (RAM): the global static space, the heap, and the stack.
- You also have an unspecified amount of space in the IO system (ROM).


## Stack
Why do we need a stack? We have functions calling functions, and every time you call a function you get a new stack frame. You keep putting frames on the stack as you call linearly, and you pop off as you return.

The addresses for any given routines are addressed relative to the stack pointer. The stack is called an automatic space because the system gets addresses for you.

## Address Spaces
There is virtual address space and physical address space (hardware). These are connected by a page table, which has a Page # and a Byte #. Why do we need page tables? Because if the compiler compiled addresses directly, then you couldn’t run multiple programs at the same time since programs might overwrite each other. Instead, the compiler assigns pages, and every program uses the same compiler.

When physical memory isn’t big enough, you go to the disk for SWAP space, which is thousands to billions of times slower.

## C Types

### Primitive Types
- Int
- Float
- Char (8-bit integer, you can mix these but compiler will complain)
- Addresses / Pointers (also ints, but you can’t mix these)

### Compound Types
- Arrays
    - Strings (special case of an array, string is just an array of characters with a null terminating character `\0`)
- Struct

### Control Structures/Statements: 
For loop, while loop, if/else, switch, assignment (=), comparison (==), and Functions. No I/O or memory management in the book.

### Levels of Programming
Application programs (highest)
    C library routines
        System calls (Operating System)
            Kernel

