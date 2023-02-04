---
layout: ../../layouts/Layout.astro
title: Computer Systems
description: Computer Systems By X
section: Books
date: January 29th, 2022
order: 3
---

# Notes from reading [Compuer Systems]().

1. [Chapter 1:](#chapter-one)
1. [Chapter 2: Representing and Manipulating Information ](#chapter-two)

# Chapter 1 <a name="chapter-one"></a>

Writing hello world in C using [VS code](https://code.visualstudio.com/docs/languages/cpp).

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

<br>The first byte has an integer value 35, which corresponds to the character. Each text line is terminated by the invisible newline character `\n` Two of these in a row would be two new lines, for example.

Files such as `hello.c` that consist exclusively of ASCII characters are known as text files. All other files are known as binary files.</br>

<br>All information in a system is represented as a bunch of bits. The only thing that distinguishes different data objects is the context in which we view them. For example, in different contexts, the same sequence of bytes might represent an integer, floating-point number, character string, or machine instruction.</br>

<br>
Our hello program stars life as a high-level C program because it can be read and understood by human beings. However, in order to run `hello.c` on the system, the individual C statements musst be translated by other programs into a sequence of low-level machine-language instructions. These instructions are then packaged in a form called an executable object program and stored as a binary disk file.</br>

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

JavaScript is an interpreted language, not a compiled language. With a language such as C, it needs to be compiled before it is run. The source code is passed through a program called a compiler, which translates it into bytecode that our machine understands and can then execute.

JS has no compilation step. Instead, an interpreter in the browser reads over the JS code, interprets each line, and runs it.

# C Standard library

C doesn't have built-in functions, those come from the C Standard libray.
If you're in a unix-derived operation system, the C standard library ships with the OS - in our terminal we can do `man 3 printf` and look at the manual.

# Chapter 2: Representing and Manipulating Information <a name="chapter-two"></a>

Modern computers store and process information represented as two-valued signals: bits.

3 most important representatios of numbers.

**Unsiged encodings** are based on traditional binary notation, representing numbers greater than or equal to 0.

**Two's complement** encodings are the most common way to represent **signed integers**, that is, numbers that may be either positive or negative.

**Floating-point** encodings are a base-2 version of scientific notation for represeting real numbers. Computers implement arithmetic operations (addition, multiplication for example) with these different representations, similar to the corresponding operations on integers and real numbers.

Computer representations use a limited number of bits to encode a number, and hence some operations can overflow when the results are too large to be represented.

2.1 Information storage

Rather than accessing individual bits in memory, most computers use blocks of 8 bits, or bytes, as the smallest addressable unit of memory. A machine level program views memory as a very large array of bytes, referred to as **virtual memory**.

Every bye of memory is identified by a unique number, known as its address, and the set of all possible value addresses is known as the virtual space address.

The virutal space address is just a conceptual image presented to the machine-level program. The actual implementation uses a combination of dynamic random access memory (DRAM), flash memory, disk storage, special hardware, and operating system software to provide the program with what appears to be a monolothic byte array.

The compiler and run-time system partitions this memory space into more managable units to store the different program objects, that is, program daa, instructions and control information. Varous mechanisms are used to allocate and manage the storage for different parts of the program. The management is all performed within the virtual address space. For example, the value of a pointer in C - whether it points to an integer, a structure, or some other program object - is the virtual address of the first byte of some block of storage. The C compiler also associates type info with each pointer, so that it can generate different machine-level code to access the value stored at the location designated by the pointer depending on the type of that value.

**Pointers in C.**

Pointers provide the mechanism for referencing elements of data structures, including arrays. Just like a variable, a pointer has two aspects: is value and its type. The value indictates the location of some object, while its type indicates what kind of object (e.g., integer or floating point number) is stored at their location.

**Hexadeciaml notation.**

<br>A single byte consists of 8 bits. In binary notation, its value ranges from 00000000<sup>2</sup> to 11111111<sup>2</sup>. When viewed as a decimal integer, its value ranges from 0<sup>10</sup> to 255<sup>10</sup>.</br>

<br>Neither notation is very convenient for describing bit patterns. Binar notation is too verbose, while decimal notiation amkes it tedious to convert to and from bit patterns. Instead, we wite bit patterns as base-16, or hexadecimal numbers. Hexadeimal (or "hex") uses

Written in hexadecimal, the value of a single byte can range from 00<sup>16</sup> to FF<sup>16</sup>. In C, numeric constants starting with 0x or 0X are interpreted as being in hexadecimal.

 <img src="/assets/hex-to-binary.png" alt="Image.">

Given a binary number, you can convert it to hexadecimal by first splitting it into groups of 4 bits each. Note, however, that if the total number of bits is not a multiple of 4, you should make the leftmost group be the one with fewer than 4 bits, effectively padding the number with leading zeros.

**Hex to binary.**

You can convert hex to binary by expanding each hexadecimal digit. Example:

**Practice problems.**

Change 0x39A7F8 to binary.

In binary this is 1110011010011111111000.

## Other resources

Teachyourselfcs.com

https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/pages/c1/c1s2/
