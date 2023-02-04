---
layout: ../../layouts/Layout.astro
title: Computation Structures
description: MIT's Computation Structures
section: Courses
date: January 29th, 2022
order: 3
---

# Notes from reading [Compuation Structures](https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/pages/c1/c1s2/) by Chris Terman.

1. [Chapter 1:](#chapter-one)
1. [Chapter 2: Representing and Manipulating Information ](#chapter-two)

# Chapter 1 <a name="chapter-one"></a>

```c
#include <stdio.h>
int main() {
  printf("Hello, World!\n");
}
```

Entropy

In information theory, the entropy H(X) is the average amount of information contained in each piece of data received about the value of X.

An encoding is an unambiguous mapping between bit strings and the set of possible data.

Encoding positive integers

It is starightforward to encode positive integers as a sequence of bits. Each bit is assigned a weight. Ordered from right to the left, these weights are increasing powers of 2.

Signed magnitude method.

Express -6.

First we find out what 6 is. We use a 4-bit binary to do so.

6 is 0 1 1 0.
