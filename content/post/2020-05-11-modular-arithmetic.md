---
date: 2020-05-11T00:00:00Z
title: Modular Arithmetic
tags:
  - Number Theory
  - Arithmetic
  - Algebra
authors:
  - Aurélien Ooms
---

Positional notation.

An arbitrary precision integer on a computer is represented as a list of
digits (limbs). They are just bigger. Today's computers can hold 64 bits per
limb.

Modular arithmetic consists in applying addition and multiplication to integers
modulo a certain number \\(n\\).

Given an implementation of addition, multiplication, and division on the
integers, we can emulate addition or multiplication modulo \\(n\\) by performing
the corresponding operation on integers then taking the result modulo \\(n\\).

However, taking the modulo is usually more expensive than multiplication: the
schoolbook algorithm for division takes quadratic time and the divide and
conquer solution [1] solves the problem with
up to \\(\log n\\) input size multiplications:
one with the schoolbook method,
two with Karatsuba multiplication,
roughly 2.6 with Toom-Cook \\(k=3\\),
\\(\\log n / 2\\) with \\(n \\log n\\)-time multiplication,
and
\\(\\log n\\) with linear-time multiplication (no algorithm is known to achieve
this).

To be fair, for a certain range of input sizes, this divide and conquer
approach to division is faster than the methods we are presenting here, in
particular for small input sizes that should be handled with the schoolbook
multiplication method or Karatsuba's algorithm.

Note that depending on the base being used to represent our numbers, some
division and modulo operations can be done amazingly fast: when representing
numbers in base 10 for instance, that number modulo 10 is simply his last
digit.

We are interested in a technique called Montgomery trick. This technique shows
that, as long as \\(gcd(R,N) = 1\\) with \\(R>N\\) it is possible to trade
operations modulo \\(N\\) for operations modulo \\(R\\).
Hence, if modulo \\(R\\) can be done efficiently, so can modulo \\(N\\).

### The Trick

If \\(gcd(R,N)=1\\) then there exists integers R' and N' such that \\(RR' + NN' =
1\\) (Bezout's identity). Then \\(NN' = 1 - RR'\\) which means \\(N'\\) is the inverse
of \\(N\\) modulo \\(R\\).

Given an input \\(T \\in [0, RN-1]\\),
informally,
we can compute the *pseudo-quotient* \\(q = T/N \mod R\\) by \\(q = TN' \mod R\\). Then
the *pseudo-rest* of this *pseudo-division* by \\(N \mod R\\) is \\(r = T - qN = T -
TNN' = 0 \mod R\\).

\\[
\begin{aligned}
q &= ((T \mod R) N') \mod R
\\\\ r &= TR' \mod N
\\\\ &= TR' - (qR')N
\\\\ &= (T - qN) R' = (T - qN) / R.
\end{aligned}
\\]

where the last line works since \\(r = 0 \mod R\\).

Hence multiplication by \\(R' \mod N\\) can be achieved by keeping the high digit of
\\(T - qN\\) in base \\(R\\).

  - \\(q = (T \mod R) N' \mod R\\)
  - \\(r = (T - qN) / R\\)

where \mod R corresponds to taking the lower digits and division by R
corresponds to taking the higher digits.
This involves only two multiplications:

  - \\((T \mod R) N'\\)
  - \\(qN\\)

Note that \\(q \\le R-1\\), hence \\(T - qN \\in [-(R-1)N, RN-1]\\), hence \\(r\\) is
in the range \\([-(R-1)N/R, N-1/R]\\) and since \\(r\\) is an integer this range
collapses to \\([1-N, N-1]\\).
Hence, \\(r\\) can be brought down to the representation range \\([0,N-1]\\) with
one addition.

#### Time Complexity

The trick uses two integer multiplications:
one to compute \\((T \mod R) N'\\), and one to compute
\\(qN\\). Note that all operands are smaller than \\(R\\). If
\\(R\\) is made out of \\(k\\) digits, then these multiplications are all \\(k
\\times k\\) multiplications.

Note that in the first multiplication we only care about the lower order bits
of the result, and in the second multiplication we only care about the higher
order bits of the result. This can be exploited to further reduce the overhead
of this method for relatively small inputs.

## Addition and Multiplication modulo \\(N\\)

To implement addition and multiplication easily we convert numbers \\(A\\) and
\\(B\\) to \\(AR \mod N\\) and \\(BR \mod N\\) using the standard division algorithm.
This incurs an initial conversion cost that is negligible when lots of
arithmetic operations are performed (for instance, in modular exponentiation).

Then \\(A+B\\) corresponds to \\((A+B)R \mod N = AR \mod N + BR \mod N\\) where the
last \\(\mod N\\) operations can be done with a single subtraction.

And \\(A\*B\\) corresponds to \\((A\*B)R \mod N = (AR \mod N)(BR \mod N) R' \mod N\\)
where the multiplication by \\(R' \mod N\\) is achieved through Montgomery's
trick.

[1]: https://pure.mpg.de/rest/items/item_1819444_4/component/file_2599480/content
