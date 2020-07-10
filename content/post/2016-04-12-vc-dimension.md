---
date: 2016-04-12T00:00:00Z
title: VC-dimension
url: /2016/04/12/vc-dimension/
thumbnail:
  src: https://ipfs.c.ovfefe.cf/ipfs/QmZpYeMXHBqCC1m8NtDJh82DQS8Q5YDLMPAsW3e4ZJtXTz
tags:
  - Geometry
  - VC-dimension
  - epsilon-nets
---

Definitions of VC-dimesion and $$\varepsilon$$-nets.
<!--more-->

## Definition 1 (Espilon net)
Let $$X$$ be a set, let $$\mu$$ be a probability measure on $$X$$, let
$$\mathcal{F}$$ be a system of $$\mu$$-measurable subsets of $$X$$, and let
$$\varepsilon \in [0,1]$$ be a real number. A subset $$N\subseteq X$$ is
called an $$\varepsilon$$-net for $$(X,\mathcal{F})$$ with respect to
$$\mu$$ if $$N \cap S \neq \emptyset$$ for all $$S \in \mathcal{F}$$ with
$$\mu(S) \ge \varepsilon$$.

## Definition 2 (Trace of $$\mathcal{F}$$ on $$Y$$)
Let $$\mathcal{F}$$ be a set system on $$X$$ and let $$Y \subseteq X$$. We define the
restriction of $$\mathcal{F}$$ on $$Y$$ (also called the *trace* of
$$\mathcal{F}$$ on
$$Y$$) as
$$
\mathcal{F}|_Y = \{S \cap Y \colon\, S \in \mathcal{F}\}.
$$


## Definition 3 (VC-dimension)
Let $$\mathcal{F}$$ be a set system on a set $$X$$. Let us say that a subset $$A
\subseteq X$$ is shattered by $$\mathcal{F}$$ if each of the subsets of $$A$$ can
be obtained as the intersection of some $$S \in \mathcal{F}$$ with $$A$$, i.e.,
if $$\mathcal{F}|_A = 2^{A}$$. We define the VC-dimension of
$$\mathcal{F}$$, denoted
by $$dim(F)$$, as the supremum of the sizes of all finite shattered
subsets of $$X$$. If arbitrarily large subsets can be shattered, the
VC-dimension is $$\infty$$.


## Theorem 1 (Epsilon net theorem)
If $$X$$ is a set with a probability measure $$\mu$$, $$\mathcal{F}$$ is a system of
$$\mu$$-measurable subsets of $$X$$ with $$dim(\mathcal{F}) \le d$$, $$d\ge 2$$, and
$$r \ge 2$$ is a parameter, then there exists a $$\frac{1}{r}$$-net for
$$(X,\mathcal{F})$$ with respect to $$\mu$$ of size at most $$Cdr\ln r$$, where $$C$$
is an absolute constant.


## Definition 4 (Shatter function)
We define the shatter function of a set system $$\mathcal{F}$$ by
$$
\pi_\mathcal{F}(m) = \max_{Y\subseteq X, \lvert Y \rvert = m} \lvert \mathcal{F}|_Y
\rvert.
$$


## Lemma 1 (Shatter function lemma)
For any set system $$\mathcal{F}$$ of VC-dimension at most $$d$$, we have
$$\pi_\mathcal{F}(m)
\le \Phi_d(m)$$ for all $$m$$, where $$\Phi_d(m) = \binom{m}{0} +
\binom{m}{1} + \cdots + \binom{m}{d}$$.

## Proposition 1
Let $$\mathbb{R}[x_1,x_2,\ldots,x_d]_{\le D}$$ denote the set of all real
polynomials in $$d$$ variables of degree at most $$D$$, and let
$$
\mathcal{P}_{d,D} = \{\{x\in \mathbb{R}^d \colon\, p(x) \ge 0\}\colon\, p \in
\mathbb{R}[x_1,x-2,\ldots,x_d]_{\le D}\}.
$$
Then $$dim(\mathcal{P}_{d,D}) \le \binom{d+D}{d}$$.

## Proposition 2
Let $$F(X_1,X_2,\ldots,X_k)$$ be a fixed set-theoretic expression (using
the operations of union, intersection, and difference) with variables
$$X_1,X_2,\ldots,X_k$$ standing for sets.
Let $$\mathcal{S}$$ be a set system on a ground set $$X$$ with
$$dim(\mathcal{S}) = d <
\infty$$. Let
$$
\mathcal{T} = \{F(S_1,S_2,\ldots,S_k) \colon\, S_1,S_2,\ldots,S_k \in
\mathcal{S}\}.
$$
Then $$dim(\mathcal{T}) = O(kd\ln k)$$.
