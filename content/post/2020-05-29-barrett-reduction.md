---
draft: true
date: 2020-05-29T17:02:08+02:00
title: Barrett Reduction
tags:
  - Number Theory
  - Arithmetic
  - Algebra
authors:
  - Aurélien Ooms
---

We want to compute `x mod n`. Let `q = floor(x/n)` then `x - qn = x mod n` and
`0 <= x - qn < n`. This requires one multiplication and one subtraction once
`q` is known. Using multiprecision floating point arithmetic, we could
precompute `1/n` and compute `q` with a single multiplication. We just need to
figure exactly how much precision is required.

Let `r` be the radix used to represent integers, Barrett reduction approximates
`1/n` with `m/r^k` for some `k` (`m` can be precomputed as `m = floor(r^k/n)`).
Dividing by `n` amounts then to multiplying by `m` then dividing by `r^k` (a
shift by `k` places using representation in base `r`). Provided we choose `k`
appropriately, this will give the correct result modulo `n`.

The error of our approximation of `1/n` is `e = 1/n - m/r^k`.
Let `q' = floor(x m / r^k) <= q` and compute `x' = x - q'n`.
Observe that `x/n` might have a fractional value `f` anywhere between `.0` and
`.999...`.
As long as \\(q - q' <= xe + f < 2\\)
\\(x'\\) yields the correct result modulo `n` with a value between `0` and `2n-1`.
The actual congruence class can be obtained with a most one subtraction.

Since `f` can be as high as `1`, we want `xe < 1`, and hence `e < 1/x`.
This gives the bound required on `k` for the reduction to work: we have `m =
floor(r^k/n)` and `e = 1/n - m/r^k < 1/x`, hence

    1/n - m/r^k < 1/x
    m/r^k > 1/n - 1/x
    m/r^k > (x - n) / xn
    r^k < m xn / (x - n)

For instance if `n = r^l` with `l <= k` then `r^k/n` is an integer and `m =
r^k/n`, hence

    1 < x / (x - n)

Hence `n != 0`, `x > n`. This applies for all cases where `n` divides `r^k`.

What if `n` does not divide `r^k`? Then `m = floor(r^k/n) > r^k/n - 1`. Thus we
can guarantee that `r^k < mxn / (x - n)` if

    r^k < r^k x / (x - n) - xn / (x - n)
    1 < x / (x - n) - xn / (x - n) / r^k
    xn / (x - n) / r^k < x / (x - n) - 1 = (x - (x - n)) / (x - n) = n / (x - n)
    r^k > x
    k > log x / log r

Which means that `k` must be at least the number of words in `x`.
Note that we divide by `x-n` so `x > n`.

#### Time Complexity

The reduction uses two multiplications:
the first one multiplies \\(x\\) with \\(m\\),
the second one multiplies \\(q'\\) by \\(n\\).
If \\(n\\) consists of \\(k'\\) digits, then reducing a \\(k=2k'\\) digit number
modulo \\(n\\) costs one \\(2k' \\times k'\\) multiplication and one \\(k' \\times k'\\)
multiplication. This is slightly worse than Montgomery's reduction.

Note that since \\(q' = \\lfloor x m / r^k \\rfloor\\), we only care about the
higher order digits of \\(xm\\). Similarly, when computing \\(q'n\\), we know by the
error analysis that the higher order digits will be equal to those of \\(x\\), so
we only need to compute the lower order digits of \\(q'n\\).

However those gains tend to zero as more and more efficient multiplication
subroutines are used for large \\(n\\).

PS: Barrett reduction is more popularly known as reducing a number `0 <= x <
n^2` modulo `n` with `r=2`. Then we have `2^k > n^2` which gives the usual
approximation `floor(4^k'/n)/4^k'` of `1/n` with `k = 2k'`.

PPS: Barrett reduction not only computes the remainder but also the quotient.
The error in the quotient is at most one as seen above. We can find the
correct value by checking that the modulo is in the correct range with an
additional multiplication, exactly as if we were computing the correct
congruence class for the modulo. I don't see how to save the last
multiplication. We know that the `x`'s such that `q - q' = 1` are the `x`'s such
that `xe + f >= 1`. However, `f` is not monotone in `x`. Although `xe + f` is
more and more likely to be above `1` as `x` increases, there is not clear-cut
threshold that characterizes when the quotient must be corrected.

PPPS: However, in the particular case where the division is exact, i.e. `x = 0
mod n`, we have that `f` is 0. Hence, if we know that `n` divides `x` we can
compute the quotient with a single multiplication by `m`.

PPPPS: Since \\(\\lfloor \\frac{r^l}{n} \\rfloor\\) with \\(l <= k\\)
corresponds to a prefix of the digits of \\(\\lfloor \\frac{r^k}{n}
\\rfloor\\), we can precompute \\(m\\) for a large \\(k\\) but only use those digits
that are necessary depending on the size of \\(x\\).

See https://en.wikipedia.org/wiki/Barrett_reduction
See https://www.nayuki.io/page/barrett-reduction-algorithm
See https://pure.mpg.de/pubman/faces/ViewItemOverviewPage.jsp?itemId=item_1819444
