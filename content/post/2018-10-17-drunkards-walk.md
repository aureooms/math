---
date: 2018-10-17T00:00:00Z
title: The Drunkard's Walk
url: /2018/10/17/drunkards-walk/
thumbnail:
  src: https://ipfs.c.ovfefe.cf/ipfs/QmSAXMJTDSRbyNyJZWhXUrdXuKiCxD6p6H9ths64L32dQm
  caption: The Drunkard's Pilgrimage
tags:
  - Recurrences
authors:
  - Aurélien Ooms
---

A drunkard is zigzagging home. At every steps forward (or backward) he is
making, he also moves $$1$$ step to the left with probability $$p$$ and $$1$$
step to the right otherwise. He starts $$i$$ steps to the right of a river. What is
the expected number of steps forward before he falls into the river?

<!--more-->

We model the expected number of steps before the drunkard falls into the river
by $$A(i)$$ when the drunkard starts $$i$$ steps to the right of the river.

If the drunkard starts his walk after having fallen into the river,
then he does not even need to move
$$
A(0) = 0
$$

The statement of the problem allows us to express $$A(i)$$ with respect to its
neighbouring values.
$$
A(i) = p A(i-1) + (1-p) A(i+1) + 1
$$

Another important point is that the expected number of steps before the fall is
the same as the sum of the expected number of steps before moving one step
towards the river by linearity of expectation. Hence,
$$
A(i) = i A(1)
$$

Solving for $$i=1$$,
$$
A(1) = p A(0) + (1-p) A(2) + 1
$$

$$
A(1) = (2-2p) A(1) + 1
$$

$$
A(1) (2p - 1) = 1
$$

$$
A(1) = \frac{1}{2p-1}
$$

And finally
$$
A(i) = \frac{i}{2p-1}
$$

The problem can also be stated with the drunkard moving forward with
probability $$p$$ and backwards otherwise. Then ask what is the expected time
before the drunkard reaches home (provided forward means in the direction of
his home).
