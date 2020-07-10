---
date: 2015-06-29T00:00:00Z
title: Inverse sum equations
url: /2015/06/29/inverse-sum/
thumbnail:
  src: https://ipfs.c.ovfefe.cf/ipfs/QmNnXTqBHeNReAhAE9svPrr5bcXqerc71qb9LJYUhF99h9
tags:
  - Brute Force
  - Algorithms
  - Systems of Inequalities
---

We are given $$k > 0 \in \mathbb{R}$$ and $$a_1, a_2, \ldots, a_n \ge 1 \in \mathbb{N}$$ such that

$$
a_1 < a_2 < \cdots < a_n.
$$

We want to solve the following equation

$$
\frac{1}{a_1} +
\frac{1}{a_2} +
\cdots +
\frac{1}{a_n} = k.
$$

<!--more-->
Note that we have

$$
\frac{1}{a_1} >
\frac{1}{a_2} >
\cdots >
\frac{1}{a_n}
$$

and thus

$$
n \cdot \frac{1}{a_1} >
\frac{1}{a_1} +
\frac{1}{a_2} +
\cdots +
\frac{1}{a_n} = k.
$$

Hence,

$$a_1 < \frac{n}{k}$$

and we only have a finite number of candidate solutions to test.

  - [Brute-force search implementation](https://cocalc.com/projects/00bf44da-33dd-49ad-a9d5-54c2182f171e/files/inverse-sum.sagews)

Inspired from an exercise in

> BÓNA, Miklós. A walk through combinatorics: an introduction to enumeration and graph theory. World scientific, 2011.
