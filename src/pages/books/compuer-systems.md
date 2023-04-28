---
layout: ../../layouts/Layout.astro
title: Computer Systems
description: TBD
section: Books
order: 3
---

# Notes from reading [Compuer Systems.).

1. [Chapter 1:](#chapter-one)
1. Chapter 2: Representing and Manipulating Information ](#chapter-two)

# Chapter 1 <a name="chapter-one"></a>

Writing hello world in C using Visual Studio code: (https://code.visualstudio.com/docs/languages/cpp).

```c
#include <stdio.h>
int main() {
  printf("Hello, World!\n");
}
```

Using the default compiler that ships with Mac OS - Clang.
Compile the file:
``cc hello.c`
CC for 'C compiler.'
Execute the file (now that it's an executable).
`./hello`

Our hello world program begins life as a source program (or source file) hat we create with our editor and save in a text fiel called `hello.c`. The source program is a sequence of bits, each with a value of 0 or 1, organized in 8 bit chunks called bytes. Each byte represents some text character in the program.

Most computer systems represent text characters using the ASCII standard that represents each character with a unique byte-size integer value.

<img src="/assets/hello-ascii.png" alt="Image.">

The `hello.c` program is stored in a file as a sequence of bytes. Each byte has an integer value that corresponds to some character.

The firt byte has an integer value 35, which corresponds to the character #.

Each text line is terminated by the invisible newline character `\n` Two of these in a row would be two new lines, for example.

Files such as `hello.c` that consist exclusively of ASCII characters are known as text files. All other files are known as binary files.

All information in a system is represented as a bunch of bits. The only thing that distinguishes different data objects is the context in which we view them. For example, in different contexts, the same sequence of bytes might represent an integer, floating-point number, character string, or machine instruction.

Our hello program stars life as a high-level C program because it can be read and understood by human beings. However, in order to run `hello.c` on the system, the individual C statements musst be translated by other programs into a sequence of low-level machine-language instructions. These instructions are then packaged in a form called an executable object program and stored as a binary disk file.

On a Unix system, the translation from source file to object file is performed by a compiler driver.

<img src="/assets/compiler-driver-steps.png" alt="Image.">

Here the GCC compiler driver reads the source file `hello.c`, and translaes it into an executable object file, `hello`. The translation is performed in the sequence of 4 phases shown aove. The programs that perform the 4 phase (preprocessor, compiler, assembler, and linker) are known collectively as the compilation system.

**Preprocessing phase**. The preprocessor (cpp) modifies the original C program according to directives that begin with the '#' character. For example, the `#include <stdio.h>` command in line 1 of `hello.c` tells the preprocessor to read the contents of the system header file `stdio.h` and insert it directly into the program text. The `stdio.h` heaeder files lets us perform input and output operations in C.

**Compilation phase.** The compiler (cc1) translates the text file `hello.i` into the text file `hello.s`, which contains an assembly-language program. This program include the following defintion of function `main`:

<img src="/assets/compilation-phase.png" alt="Image.">

Each of lines 2-7 in this defintion describe one low-level macine-language instruction in a textual form. Assembly langauge is useful because it provides a common output language for different compilers for different high-level-languages. For example, C compilers and Fortran compilers both generate output files in the same assembly language.

**Assembly phase.** Next, the assembler (as) translates `hello.s` into machine-language instructions, packages them in a form known as relocatable object program, and stores the result in the object file `hello.o`. This file is a binary file containing 17 bytes to encode the instructions for function `main`. If we view this file with our text editor, it appears to be gibberish.

**Linking phase**. The `printf` function is part of the standard C library provided by every C compiler. The `printf` function resides in a seperate precompiled object file called `printf.o`, which must get merged with our `hello.o` program. The linker handles this merging. The result is the `hello` file, which is an execuable object file (or simply executable) that is ready to be loaded into memory and executed by thy system.

My asides

## In relation to JavaScript

JavaSCript is an interpreted language, not a compiled language. With a language such as C, it needs to be compiled before it is run. The source code is passed through a program called a compiler, which translates it into bytecode that our machine understands and can then execute.

JS has no compilation step. Instead, an interpreter in the browser reads over the JS code, interprets each line, and runs it.

## C Standard library

C doesn't have built-in functions, those come from the C Standard libray.
If you're in a unix-derived operation system, the C standard library ships with the OS - in our terminal we can do `man 3 printf` and look at the manual.

# Chapter 2: Representing and Manipulating Information <a name="chapter-two"></a>

Modern computers store and process information represented
