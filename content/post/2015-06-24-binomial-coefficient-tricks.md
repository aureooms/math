---
date: 2015-06-24T00:00:00+02:00
title: Binomial coefficient tricks
thumbnail:
  src: https://ipfs.c.ovfefe.cf/ipfs/QmQeJRjHamrvs9a7R1zrsJUTTDWsv6BBW79GQm2Yc6Z8gT
tags:
  - Identities
duration: PT30M
categories:
  - POST
  - TEST
---

$$
\binom{n}{k} = \binom{n}{n-k}
$$

holds because keeping \\(k\\) elements from \\(n\\) elements is equivalent
to discarding \\(n-k\\) elements from \\(n\\) elements.

<!--more-->
$$
\sum_{k=0}^{n} \binom{n}{k} \binom{n}{n-k} = \binom{2n}{n}
$$

holds because choosing \\(n\\) elements from \\(2n\\)
elements is equivalent to first choosing \\(k\\) elements
from a first set of \\(n\\) elements and then choosing \\(n-k\\)
elements from a second set of \\(n\\) elements. Hence,

$$
\sum_{k=0}^{n} \binom{n}{k}^2 = \binom{2n}{n}.
$$
