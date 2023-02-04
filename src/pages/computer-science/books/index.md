---
layout: ../../../layouts/Layout.astro
title: Test
description: This is some intro for this doc. It's styled slightly different.
section: Getting Started
order: 2
---

Khan academy - Number Systems and Binary.

We are familiar with base 10. The 'decimal' number system. Why 10? We have 10 fingers.

`0 1 2 3 4 5 6 7 8 9`

These are the 10 symbols that we came up with.

Base 2 - the binary system - is the basis of all modern computing.

In binary you have 2 symbols: `0 1`.

Computers are doing operations in binary underneath everything.

Think in powers of 2 instead of powers in 10 when using binary.

PIC

What does this mean?

This means that you have one `128`, one `64`, one `32`, no `16`, no `8`, one `4`, one `2`, and one `0`.

128 + 64 + 32 + 4 + 2 + 1 = 231.

11100111.

Converting decimal to binary.

Turn 13 from decimal representation to binary representation.

Deconstruct the number 13 as the sum of powers of 2. What powers of 2 do you need to make up this numer?

2<sup>0</sup> = 1
2<sup>1</sup> = 2
2<sup>2</sup> = 4
2<sup>3</sup> = 8
2<sup>4</sup> = 16

What's the largest power of 2 that is less than or equal to 13? 8.

13 = 8 + 5.

5 is not a power of 2, so we need to keep deconstructing.

What's the largest power of 2 that is less than or equal to 5? It's 4.

13 = 8 + 4 + 1.

We have 2<sup>3</sup>, 2<sup>2</sup> and 2<sup>0</sup>. We have 1 eight, 1 four, and 1 one.

 <img src="/assets/binary-to-decimal.png" alt="Image.">
Why is this helpful? Let's go into binary mode.

 <img src="/assets/binary-to-decimal-two.png" alt="Image.">

Now look at empty places for one, two, four, and eight.

Going from the right to the left:

There is 1 in the ONES place. There is 0 in the TWOS places. There is 0 in the twos places. There is 1 in the four place. There is 1 in the eight place. Now we have 1101. 13 in binary.

We can do this for 21.

First break 21 down into power of 2.

21 = 16 + 4 + 1.

Now from right to left, by powers of 2, see how many numbers above fit in the binary slots. Can ask "Starting at 1, are there any 1s? Yes - write a 1. Then to the left - are there any twos? No, write a 0 in front of the 1. Are here any 4s? Yes, write another 1. Are there any eights? No, write a 0. Lastly, in the front, are there any 16s? Yes, write a one. So we have:

10101

Another way to convert decimal to binary.

Take your number - 13.

Divide by 2 until you get to 1. Ignore the remainder.

13 / 2 = 6.

6/ - 2 = 1.

Now take all the numbers you got including 13.

1 3 6 13.

Beneath them, write a 1 below any number that is odd, and a zero below any number that is even. 1101. 13 is 1101 in binary.

Bits and bytes

What does it mean for a value to "be" a certain number of bits?

In most contexts our decision is to say if we want to store/transmit an integer, we decide how many bits we allow the integer we represent. Is it 16 or 32 bits that we are allowing this integer to reside in?

Let's say that we add 2 integers together.
The CPU expects those numbers to reside in registers which on a modern machine are 64 bits. You may decide you want to use only 32 bits (For instance to be backyards compatible with another machine, or maybe you want to store this in an array that you want to take up less space in memory).

Say we have 4 bit integers.
4 spots, positive: \_ \_ \_ \_
Now we have 4 places for our bits. All these are zeros or ones. What happens if you add a 1 to this?
Well, we no longer have space, as a 4 bit integer. So now we have overflow. So in most contexts this becomes a zero.

Example - Ariane flight V88 blew up due to diff reasons. One aspect was squeezing a number ino a 16-bit integer.

<br>In Python, authors decided that large numbers should be well handled in a way that users don't need to think about overflow. Ruby has this too. Many languages have this as a library w/ big numbers.</br>

**Hexadecimal number system**.

With hex, we have a base of 16. 16 places for our numbers.

We use 0-9 and then the first 6 letters of the alphabet.

A is 10, B is 11, C is 12 and so on.

How would we represent 231 in hexadecimal?

The number 231 in hexadecimal is the number E7.

 <img src="/assets/hexadecimal-system.png" alt="Image.">

The 7 in E7 is the ones place, that is, 16<sup>0.</sup>. So the first place where we have the 7 represents 16 to the zero power.

E is in the sixteens place. This is E sixteens + 7 ones.

What is E? E is 14.

So we have 12 sixteens + 7 ones. That is 14 x 16 = 224, plus 7 = 231.

When you have a high base, you can represent bigger numbers, faster.

We see hexadecimal used with CSS.

What is FF in decimal representation?

The second F is in the ones place (16<sup>0</sup> = 1) and the second F on the left is in the 16s place (16<sup>2</sup> = 16), which means we have F ones and F 16s. F is 15. So we have 15 ones and 15 sixteens. 15 times 16 is 240, plus 15 ones is 255. FF = 255.

**Converting from deciaml to hexadecimal representation.**

Convert 2,000 in binary to hexadecimal.

Remember our powers of 16.

 <img src="/assets/hexadecimal-ex.png" alt="Image.">

Then decompose. What's the largest power of 16 that is less than or equal to 2,000?

256. And how many times does 256 go into 2,000?

Divide 2000 / 256:

2000 / 256 = 7.8125. 256 goes into 2,000 7 times.

So what is left over? 2000 - 7 \* 256.

Now, we say:

2000 - 7 \* 256 = 208. So we have 208 left over.

Now we have:

2000 = 7 \* 256 + 208.

How many sixttens go into 208? 208 / 16 = 13.

Now we have broken this down into multiples of powers of 16.

So we have 7 256s, and we have 13 16s.

So we have 7D0.

0 is in the 1s place as we have no zeros. In the 16s place, we have 13 sixttens, which is D. We have 7 256s, which is 7. This is 7DO.

**Binary to hex.**

Take 67 in decimal, 1000011 in binary.

Convert it to hex. Take the last 4 numbers, 0011. In binary this means we have 1 one, 1 two, zero fours and zero eights. That is 1 + 2 = 3.

For the first 3 numbers, we have 0 16s, 0 32s, and 1 64.

So we have 64 + 3 which is 67.
