---
date: 2016-01-17T00:00:00+01:00
title: <span class="math">\(d\)</span> hyperplanes intersection bounds
url: /2016/01/17/d-hyperplanes-intersection-bounds
thumbnail:
  src: https://ipfs.c.ovfefe.cf/ipfs/QmPAdhtD5ojLZP69nVe9EbHgAhon7BDnQbxic9nGSBk5cv
tags:
  - Geometry
  - Linear Algebra
---

We bound the position of the $$0$$-cells of an arrangement of hyperplanes in
$$\mathbb{R}^d$$. This allows, for example, to build an hypercube that
intersects all cells of the arrangement. Such an hypercube must contain at
least one point of each cell of the arrangement. When $$q > 0$$, in order to
fix which point of a $$q$$-cell we want to include in the hypercube, it
suffices to add the $$n$$ hyperplanes of equation $$x_i = 0$$ to the
arrangement. With those additional hyperplanes, the arrangement is such that
each $$q$$-cell of the arrangement with $$q > 0$$ contains a
$$0$$-cell of the arrangement, hence, we only need the hypercube to
intersect, for each $$0$$-cell $$\nu$$ of the arrangement, an hypersphere
of center $$\nu$$ and arbitrarily small radius. The inequalities of the
polyhedral set defining our hypercube will thus only depend on the position of
the $$0$$-cells of our arrangement.

<!--more-->
We thus bound the components of those vertices. Since the $$0$$-cells of our
arrangement are intersections of $$n$$ intersecting and linearly independent
hyperplanes, we focus on the solutions of systems of $$n$$ linear equations
in $$\mathbb{R}^n$$.
Let us begin with a few examples to build some intuition.

## Examples

### First example: $$a x + b = 0$$

If $$a \neq 0$$ then

$$
	a x + b = 0 \iff x = -\frac{b}{a}.
$$

### Second example: $$a x + b y + c = 0$$

If $$
\begin{vmatrix}
a & b \\
d & e
\end{vmatrix} \neq 0 $$
then to solve

$$
\left\lbrace\begin{aligned}
a x + b y + c &= 0\\
d x + e y + f &= 0
\end{aligned}\right.,
$$

we can use the following (implied) equations which are true for all
$$\lambda,\mu \in \mathbb{R}$$

$$
\begin{aligned}
	(a+\lambda d) x + (b + \lambda e ) y + ( c + \lambda f ) &= 0\\
	(\mu a+ d) x + (\mu b +  e ) y + ( \mu c + f ) &= 0.
\end{aligned}
$$

We can find $$x$$ by making $$y$$ disappear. Since $$
\begin{vmatrix}
a & b \\
d & e
\end{vmatrix} \neq 0 $$ we cannot have $$b$$ and $$e$$ equal to zero
simultaneously so either $$e \neq 0$$ and

$$
\begin{aligned}
\lambda = -\frac{b}{e} \implies
(a - \frac{b}{e} d) x +
(b - \frac{b}{e} e) y +
(c - \frac{b}{e} f) & = 0\\
(ae - bd) x +
(be - be) y +
(ce - bf) & = 0,
\end{aligned}
$$

or $$b \neq 0$$ and

$$
\begin{aligned}
\mu = -\frac{e}{b} \implies
(-\frac{e}{b}a + d) x +
(-\frac{e}{b}b + e) y +
(-\frac{e}{b}c + f) & = 0\\
(ae - bd) x +
(be - be) y +
(ce - bf) & = 0,
\end{aligned}
$$

hence, in either case

$$
x = -\frac{ce - bf}{ae-bd}
= +\frac{
\begin{vmatrix}
b & c \\
e & f
\end{vmatrix}
}{
\begin{vmatrix}
a & b \\
d & e
\end{vmatrix}
}.
$$

Similarily, we can find $$y$$ by making $$x$$ disappear. Since $$
\begin{vmatrix}
a & b \\
d & e
\end{vmatrix} \neq 0 $$ we cannot have $$a$$ and $$d$$ equal to zero
simultaneously so either $$d \neq 0$$ and

$$
\begin{aligned}
\lambda = -\frac{a}{d} \implies
(a - \frac{a}{d} d) x +
(b - \frac{a}{d} e) y +
(c - \frac{a}{d} f) & = 0\\
(ad - ad) x +
(bd - ae) y +
(cd - af) & = 0,
\end{aligned}
$$

or $$a \neq 0$$ and

$$
\begin{aligned}
\mu = -\frac{d}{a} \implies
(-\frac{d}{a}a + d) x +
(-\frac{d}{a}b + e) y +
(-\frac{d}{a}c + f) & = 0\\
(ad - ad) x +
(bd - ae) y +
(cd - af) & = 0,
\end{aligned}
$$

hence, in either case

$$
y = -\frac{cd - af}{bd-ae}
= -\frac{
\begin{vmatrix}
a & c \\
d & f
\end{vmatrix}
}{
\begin{vmatrix}
a & b \\
d & e
\end{vmatrix}
}.
$$

## Same examples, using a better notation

Let us do it again with a better notation.

### First example: $$\alpha_{1,0} + \alpha_{1,1} x_1 = 0$$

If $$\alpha_{1,1} \neq 0$$ then

$$
	\alpha_{1,0} + \alpha_{1,1} x_1 = 0 \iff x_1 = -\frac{\alpha_{1,0}}{\alpha_{1,1}}.
$$

### Second example: $$\alpha_{1,0} + \alpha_{1,1} x_1 + \alpha_{1,2} x_2 = 0$$

If $$
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} \\
\alpha_{2,1} & \alpha_{2,2}
\end{vmatrix} \neq 0 $$
then to solve

$$
\left\lbrace\begin{aligned}
\alpha_{1,0} + \alpha_{1,1} x_1 + \alpha_{1,2} x_2 &= 0\\
\alpha_{2,0} + \alpha_{2,1} x_1 + \alpha_{2,2} x_2 &= 0
\end{aligned}\right.,
$$

we can use the following (implied) equations which are true for all
$$y_1,y_2 \in \mathbb{R}$$

$$
\begin{aligned}
	(\alpha_{1,0}+ \alpha_{2,0}y_2 ) +
	(\alpha_{1,1}+ \alpha_{2,1}y_2 ) x_1 +
	(\alpha_{1,2}+ \alpha_{2,2}y_2 ) x_2 = 0\\
	(\alpha_{1,0}y_1+ \alpha_{2,0} ) +
	(\alpha_{1,1}y_1+ \alpha_{2,1} ) x_1 +
	(\alpha_{1,2}y_1+ \alpha_{2,2} ) x_2 = 0.
\end{aligned}
$$

We can find $$x_1$$ by making $$x_2$$ disappear. Since $$
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} \\
\alpha_{2,1} & \alpha_{2,2}
\end{vmatrix} \neq 0 $$ we cannot have $$\alpha_{1,2}$$ and $$\alpha_{2,2}$$ equal to zero
simultaneously so either $$\alpha_{2,2} \neq 0$$ and

$$
\begin{aligned}
y_2 = -\frac{\alpha_{1,2}}{\alpha_{2,2}} \implies
(\alpha_{1,0} - \frac{\alpha_{1,2}}{\alpha_{2,2}} \alpha_{2,0}) +
(\alpha_{1,1} - \frac{\alpha_{1,2}}{\alpha_{2,2}} \alpha_{2,1}) x_1 +
(\alpha_{1,2} - \frac{\alpha_{1,2}}{\alpha_{2,2}} \alpha_{2,2}) x_2
& = 0\\
(\alpha_{1,0}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,0}) +
(\alpha_{1,1}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,1}) x_1 +
(\alpha_{1,2}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,2}) x_2 & = 0
\end{aligned}
$$

or $$\alpha_{1,2} \neq 0$$ and

$$
\begin{aligned}
y_1 = -\frac{\alpha_{2,2}}{\alpha_{1,2}} \implies
(-\frac{\alpha_{2,2}}{\alpha_{1,2}}\alpha_{1,0} + \alpha_{2,0}) +
(-\frac{\alpha_{2,2}}{\alpha_{1,2}}\alpha_{1,1} + \alpha_{2,1}) x_1 +
(-\frac{\alpha_{2,2}}{\alpha_{1,2}}\alpha_{1,2} + \alpha_{2,2}) x_2
& = 0\\
(\alpha_{1,0}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,0}) +
(\alpha_{1,1}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,1}) x_1 +
(\alpha_{1,2}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,2}) x_2 & = 0
\end{aligned}
$$

hence, in either case

$$
x_1 = -\frac{\alpha_{1,0}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,0}}
{\alpha_{1,1}\alpha_{2,2} - \alpha_{1,2}\alpha_{2,1}}
= -\frac{
\begin{vmatrix}
\alpha_{1,0} & \alpha_{1,2} \\
\alpha_{2,0} & \alpha_{2,2}
\end{vmatrix}
}{
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} \\
\alpha_{2,1} & \alpha_{2,2}
\end{vmatrix}
}.
$$

Similarily, we can find $$x_2$$ by making $$x_1$$ disappear. Since $$
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} \\
\alpha_{2,1} & \alpha_{2,2}
\end{vmatrix} \neq 0 $$ we cannot have $$\alpha_{1,1}$$ and $$\alpha_{2,1}$$ equal to zero
simultaneously so either $$\alpha_{2,1} \neq 0$$ and

$$
\begin{aligned}
y_2 = -\frac{\alpha_{1,1}}{\alpha_{2,1}} \implies
(\alpha_{1,0} - \frac{\alpha_{1,1}}{\alpha_{2,1}} \alpha_{2,0}) +
(\alpha_{1,1} - \frac{\alpha_{1,1}}{\alpha_{2,1}} \alpha_{2,1}) x_1 +
(\alpha_{1,2} - \frac{\alpha_{1,1}}{\alpha_{2,1}} \alpha_{2,2}) x_2
& = 0\\
(\alpha_{1,0}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,0}) +
(\alpha_{1,1}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,1}) x_1 +
(\alpha_{1,2}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,2}) x_2 & = 0
\end{aligned}
$$

or $$\alpha_{1,1} \neq 0$$ and

$$
\begin{aligned}
y_1 = -\frac{\alpha_{2,1}}{\alpha_{1,1}} \implies
(-\frac{\alpha_{2,1}}{\alpha_{1,1}}\alpha_{1,0} + \alpha_{2,0}) +
(-\frac{\alpha_{2,1}}{\alpha_{1,1}}\alpha_{1,1} + \alpha_{2,1}) x_1 +
(-\frac{\alpha_{2,1}}{\alpha_{1,1}}\alpha_{1,2} + \alpha_{2,2}) x_2
& = 0\\
(\alpha_{1,0}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,0}) +
(\alpha_{1,1}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,1}) x_1 +
(\alpha_{1,2}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,2}) x_2 & = 0
\end{aligned}
$$

hence, in either case

$$
x_2 = -\frac{\alpha_{1,0}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,0}}
{\alpha_{1,2}\alpha_{2,1} - \alpha_{1,1}\alpha_{2,2}}
= +\frac{
\begin{vmatrix}
\alpha_{1,0} & \alpha_{1,1} \\
\alpha_{2,0} & \alpha_{2,1}
\end{vmatrix}
}{
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} \\
\alpha_{2,1} & \alpha_{2,2}
\end{vmatrix}
}.
$$

## The general case

### Theorem

For all $$n > 0 \in \mathbb{N}$$, if

$$
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} & \cdots & \alpha_{1,n}\\
\alpha_{2,1} & \alpha_{2,2} & \cdots & \alpha_{2,n}\\
\vdots & \vdots & \ddots & \vdots\\
\alpha_{n,1} & \alpha_{n,2} & \cdots & \alpha_{n,n}
\end{vmatrix} \neq 0,
$$

where $$\alpha_{i,j} \in \mathbb{R}$$ for all $$(i,j) \in [n] \times
\{\,0,1,\ldots,n\,\}$$,
then the system of linear equations

$$
\left\lbrace\begin{array}{cccccccccccc}
\alpha_{1,0} &+& \alpha_{1,1} x_1 &+& \alpha_{1,2} x_2 &+& \cdots &+& \alpha_{1,n} x_n &=& 0\\
\alpha_{2,0} &+& \alpha_{2,1} x_1 &+& \alpha_{2,2} x_2 &+& \cdots &+& \alpha_{2,n} x_n &=& 0\\
\vdots &+& \vdots &+& \vdots &+& \ddots &+& \vdots &=& \vdots\\
\alpha_{n,0} &+& \alpha_{n,1} x_1 &+& \alpha_{n,2} x_2 &+& \cdots &+& \alpha_{n,n} x_n &=& 0
\end{array}\right.
$$

has a unique solution $$x=(x_1,x_2,\ldots,x_n)$$ such that for all $$i \in [n]$$

$$
x_i = (-1)^i
\frac{
\begin{vmatrix}
\alpha_{1,0} & \alpha_{1,1} & \alpha_{1,2} & \cdots & \alpha_{1,i-1} & \alpha_{1,i+1} & \cdots & \alpha_{1,n}\\
\alpha_{2,0} & \alpha_{2,1} & \alpha_{2,2} & \cdots & \alpha_{2,i-1} & \alpha_{2,i+1} & \cdots & \alpha_{2,n}\\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots\\
\alpha_{n,0} & \alpha_{n,1} & \alpha_{n,2} & \cdots & \alpha_{n,i-1} & \alpha_{n,i+1} & \cdots & \alpha_{n,n}
\end{vmatrix}
}
{
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} & \cdots & \alpha_{1,n}\\
\alpha_{2,1} & \alpha_{2,2} & \cdots & \alpha_{2,n}\\
\vdots & \vdots & \ddots & \vdots\\
\alpha_{n,1} & \alpha_{n,2} & \cdots & \alpha_{n,n}
\end{vmatrix}
}
$$

### Proof

By induction on $$n$$. We reduce the problem of finding $$x_i$$ to the
problem of finding a solution to a system of $$n-1$$ linear equations with
$$n-1$$ unknowns.

#### Base case

We already showed that it holds for $$n=1$$ and $$n=2$$ in the examples
given previously.

#### Induction

Suppose that the theorem holds up to $$n-1$$ (this is the induction
hypothesis), we show that it must also hold for $$n$$.

Fix $$i \in [n]$$, the system of equations

$$
\left\lbrace\begin{array}{cccccccccccc}
\alpha_{1,0} &+& \alpha_{1,1} x_1 &+& \alpha_{1,2} x_2 &+& \cdots &+& \alpha_{1,n} x_n &=& 0\\
\alpha_{2,0} &+& \alpha_{2,1} x_1 &+& \alpha_{2,2} x_2 &+& \cdots &+& \alpha_{2,n} x_n &=& 0\\
\vdots &+& \vdots &+& \vdots &+& \ddots &+& \vdots &=& \vdots\\
\alpha_{n,0} &+& \alpha_{n,1} x_1 &+& \alpha_{n,2} x_2 &+& \cdots &+& \alpha_{n,n} x_n &=& 0
\end{array}\right.
$$

implies for all $$y_1,y_2,\ldots,y_n \in \mathbb{R}$$ that

$$
\begin{array}{crccccccccccclccc}
 &(&\alpha_{1,0} y_1 &+& \alpha_{2,0} y_2 &+& \alpha_{3,0} y_3 &+& \cdots &+& \alpha_{n,0} y_n &)&&&\\
+&(&\alpha_{1,1} y_1 &+& \alpha_{2,1} y_2 &+& \alpha_{3,1} y_3 &+& \cdots &+& \alpha_{n,1} y_n &)&x_1&&\\
+&(&\alpha_{1,2} y_1 &+& \alpha_{2,2} y_2 &+& \alpha_{3,2} y_3 &+& \cdots &+& \alpha_{n,2} y_n &)&x_2&&\\
+&(&\vdots             &+& \vdots             &+& \vdots             &+& \ddots &+& \vdots             &)&\vdots&&\\
+&(&\alpha_{1,n} y_1 &+& \alpha_{2,n} y_2 &+& \alpha_{3,n} y_3 &+& \cdots &+& \alpha_{n,n} y_n &)&x_n&=& 0.
\end{array}
$$

Note that we can fix one of the $$y_j$$ to some arbitrary constant while the
equation remains valid.

In order to determine $$x_i$$ it suffices to make
the $$x_k \neq x_i$$ disappear. Let us choose $$\ell \in [n]$$ such that

$$
\begin{vmatrix}
\alpha_{1,1}   & \alpha_{2,1}   & \cdots & \alpha_{\ell-1,1} & \alpha_{\ell+1,1}   & \cdots & \alpha_{n,1}\\
\alpha_{1,2}   & \alpha_{2,2}   & \cdots & \alpha_{\ell-1,2} & \alpha_{\ell+1,2}   & \cdots & \alpha_{n,2}\\
\vdots          & \vdots          & \ddots & \vdots          & \vdots            & \ddots & \vdots\\
\alpha_{1,i-1} & \alpha_{2,i-1} & \cdots & \alpha_{\ell-1,i-1} & \alpha_{\ell+1,i-1} & \cdots & \alpha_{n,i-1}\\
\alpha_{1,i+1} & \alpha_{2,i+1} & \cdots & \alpha_{\ell-1,i+1} & \alpha_{\ell+1,i+1} & \cdots & \alpha_{n,i+1}\\
\vdots          & \vdots          & \ddots & \vdots          & \vdots            & \ddots & \vdots\\
\alpha_{1,n}   & \alpha_{2,n}   & \cdots & \alpha_{\ell-1,n} & \alpha_{\ell+1,n}   & \cdots & \alpha_{n,n}
\end{vmatrix} \neq 0.
$$

Such a $$\ell$$ always exists as otherwise

$$
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} & \cdots & \alpha_{1,n}\\
\alpha_{2,1} & \alpha_{2,2} & \cdots & \alpha_{2,n}\\
\vdots & \vdots & \ddots & \vdots\\
\alpha_{n,1} & \alpha_{n,2} & \cdots & \alpha_{n,n}
\end{vmatrix} = 0.
$$

Without loss of generality we could assume that $$\ell=1$$. However, for the sake
of explanation, we will introduce a new notation to handle all cases directly.

We let $$\beta_{a,b} = \alpha_{a,b}$$ for all $$a \in \{\,2,\ldots,\ell-1,\ell+1,\ldots,n\,\}$$ and all
$$b \in \{\,0,1,\ldots,n\,\}$$. We let $$\beta_{1,b} =
\alpha_{\ell,b}$$ and $$\beta_{\ell,b} = \alpha_{1,b}$$ for all $$b \in \{\,0,1,\ldots,n\,\}$$.
For all
$$a \in \{\,0,2,\ldots,\ell-1,\ell+1,\ldots,n\,\}$$ we let $$z_a =
y_a$$. We let $$z_1 = y_\ell$$ and $$z_\ell = y_1$$.

If we fix $$z_1 = 1$$, our equation remains valid and we obtain the
following system of $$n-1$$ linear equations in $$n-1$$ unknowns

$$
\left\lbrace\begin{array}{cccccccccccc}
\beta_{1,1} &+& \beta_{2,1} z_2 &+& \beta_{3,1} z_3 &+& \cdots &+& \beta_{n,1} z_n &=& 0\\
\beta_{1,2} &+& \beta_{2,2} z_2 &+& \beta_{3,2} z_3 &+& \cdots &+& \beta_{n,2} z_n &=& 0\\
\vdots &+& \vdots &+& \vdots &+& \ddots &+& \vdots &=& \vdots\\
\beta_{1,i-1} &+& \beta_{2,i-1} z_2 &+& \beta_{3,i-1} z_3 &+& \cdots &+& \beta_{n,i-1} z_n &=& 0\\
\beta_{1,i+1} &+& \beta_{2,i+1} z_2 &+& \beta_{3,i+1} z_3 &+& \cdots &+& \beta_{n,i+1} z_n &=& 0\\
\vdots &+& \vdots &+& \vdots &+& \ddots &+& \vdots &=& \vdots\\
\beta_{1,n} &+& \beta_{2,n} z_2 &+& \beta_{3,n} z_3 &+& \cdots &+& \beta_{n,n} z_n &=& 0
\end{array}\right..
$$

By our choice of $$\ell$$ we have that

$$
\begin{vmatrix}
\beta_{\ell,1}   & \beta_{2,1}   & \cdots & \beta_{\ell-1,1}   & \beta_{\ell+1,1}   & \cdots & \beta_{n,1}\\
\beta_{\ell,2}   & \beta_{2,2}   & \cdots & \beta_{\ell-1,2}   & \beta_{\ell+1,2}   & \cdots & \beta_{n,2}\\
\vdots             & \vdots         & \ddots & \vdots               & \vdots               & \ddots & \vdots\\
\beta_{\ell,i-1} & \beta_{2,i-1} & \cdots & \beta_{\ell-1,i-1} & \beta_{\ell+1,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{\ell,i+1} & \beta_{2,i+1} & \cdots & \beta_{\ell-1,i+1} & \beta_{\ell+1,i+1} & \cdots & \beta_{n,i+1}\\
\vdots             & \vdots         & \ddots & \vdots               & \vdots               & \ddots & \vdots\\
\beta_{\ell,n}   & \beta_{2,n}   & \cdots & \beta_{\ell-1,n}   & \beta_{\ell+1,n}   & \cdots & \beta_{n,n}
\end{vmatrix} \neq 0,
$$

hence, by moving the first column to the right place,

$$
\begin{vmatrix}
\beta_{2,1}   & \beta_{3,1}   & \cdots & \beta_{n,1}\\
\beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{n,2}\\
\vdots          & \vdots          & \ddots & \vdots\\
\beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{n,i+1}\\
\vdots          & \vdots          & \ddots & \vdots\\
\beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{n,n}
\end{vmatrix} \neq 0.
$$

Thus, by the induction hypothesis, our last system of equations
has a unique solution $$z=(z_2,z_3,\ldots,z_n)$$ such that for all $$j
\in [2,n]$$

$$
z_j = (-1)^{j+1}
\frac{
\begin{vmatrix}
\beta_{1,1}   & \beta_{2,1}   & \beta_{3,1}   & \cdots & \beta_{j-1,1} & \beta_{j+1,1}  & \cdots & \beta_{n,1}\\
\beta_{1,2}   & \beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{j-1,2} & \beta_{j+1,2}  & \cdots & \beta_{n,2}\\
\vdots          & \vdots          & \vdots          & \ddots & \vdots & \vdots  & \ddots & \vdots\\
\beta_{1,i-1} & \beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{j-1,i-1} & \beta_{j+1,i-1}  & \cdots & \beta_{n,i-1}\\
\beta_{1,i+1} & \beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{j-1,i+1} & \beta_{j+1,i+1}  & \cdots & \beta_{n,i+1}\\
\vdots          & \vdots          & \vdots          & \ddots & \vdots & \vdots  & \ddots & \vdots\\
\beta_{1,n}   & \beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{j-1,n} & \beta_{j+1,n}  & \cdots & \beta_{n,n}
\end{vmatrix}
}
{
\begin{vmatrix}
\beta_{2,1}   & \beta_{3,1}   & \cdots & \beta_{n,1}\\
\beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{n,2}\\
\vdots          & \vdots          & \ddots & \vdots\\
\beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{n,i+1}\\
\vdots          & \vdots          & \ddots & \vdots\\
\beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{n,n}
\end{vmatrix}
}.
$$

Now that the $$x_k \neq x_i$$ disappeared, we have


$$
\begin{array}{crccccccccccclccc}
&(&\beta_{1,0} &+& \beta_{2,0} z_2 &+& \beta_{3,0} z_3 &+& \cdots &+& \beta_{n,0} z_n &)&&&\\
+&(&\beta_{1,i} &+& \beta_{2,i} z_2 &+& \beta_{3,i} z_3 &+& \cdots &+& \beta_{n,i} z_n &)&x_i&=& 0,
\end{array}
$$

hence,

$$
x_i = -\frac{
\beta_{1,0} + \beta_{2,0} z_2 + \beta_{3,0} z_3 + \cdots + \beta_{n,0} z_n
}
{
\beta_{1,i} + \beta_{2,i} z_2 + \beta_{3,i} z_3 + \cdots + \beta_{n,i} z_n
},
$$

that is, by replacing the $$z_j$$ by their respective values,

$$
x_i = -\frac{
\begin{vmatrix}
\beta_{1,0}   & \beta_{2,0}   & \beta_{3,0}   & \cdots & \beta_{n,0}\\
\beta_{1,1}   & \beta_{2,1}   & \beta_{3,1}   & \cdots & \beta_{n,1}\\
\beta_{1,2}   & \beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{n,2}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,i-1} & \beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{1,i+1} & \beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{n,i+1}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,n}   & \beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{n,n}
\end{vmatrix}
}
{
\begin{vmatrix}
\beta_{1,i}   & \beta_{2,i}   & \beta_{3,i}   & \cdots & \beta_{n,i}\\
\beta_{1,2}   & \beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{n,2}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,i-1} & \beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{1,i+1} & \beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{n,i+1}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,n}   & \beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{n,n}
\end{vmatrix}
},
$$

which we can rearrange by swapping rows of the second determinant to get

$$
x_i = -\frac{
\begin{vmatrix}
\beta_{1,0}   & \beta_{2,0}   & \beta_{3,0}   & \cdots & \beta_{n,0}\\
\beta_{1,1}   & \beta_{2,1}   & \beta_{3,1}   & \cdots & \beta_{n,1}\\
\beta_{1,2}   & \beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{n,2}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,i-1} & \beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{1,i+1} & \beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{n,i+1}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,n}   & \beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{n,n}
\end{vmatrix}
}
{
(-1)^{i-1}
\begin{vmatrix}
\beta_{1,2}   & \beta_{2,2}   & \beta_{3,2}   & \cdots & \beta_{n,2}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,i-1} & \beta_{2,i-1} & \beta_{3,i-1} & \cdots & \beta_{n,i-1}\\
\beta_{1,i}   & \beta_{2,i}   & \beta_{3,i}   & \cdots & \beta_{n,i}\\
\beta_{1,i+1} & \beta_{2,i+1} & \beta_{3,i+1} & \cdots & \beta_{n,i+1}\\
\vdots         & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{1,n}   & \beta_{2,n}   & \beta_{3,n}   & \cdots & \beta_{n,n}
\end{vmatrix}
},
$$

that is, by the fact that $$\mathop{det}(M) = \mathop{det}(M^T)$$,

$$
x_i = (-1)^i
\frac{
\begin{vmatrix}
\beta_{1,0} & \beta_{1,1} & \beta_{1,2} & \cdots & \beta_{1,i-1} & \beta_{1,i+1} & \cdots & \beta_{1,n}\\
\beta_{2,0} & \beta_{2,1} & \beta_{2,2} & \cdots & \beta_{2,i-1} & \beta_{2,i+1} & \cdots & \beta_{2,n}\\
\vdots       & \vdots       & \vdots       & \ddots & \vdots         & \vdots         & \ddots & \vdots\\
\beta_{n,0} & \beta_{n,1} & \beta_{n,2} & \cdots & \beta_{n,i-1} & \beta_{n,i+1} & \cdots & \beta_{n,n}
\end{vmatrix}
}
{
\begin{vmatrix}
\beta_{1,1} & \beta_{1,2} & \cdots & \beta_{1,i-1} & \beta_{1,i} & \beta_{1,i+1} & \cdots & \beta_{1,n}\\
\beta_{2,1} & \beta_{2,2} & \cdots & \beta_{2,i-1} & \beta_{2,i} & \beta_{2,i+1} & \cdots & \beta_{2,n}\\
\vdots       & \vdots       & \ddots & \vdots         & \vdots       & \vdots         & \ddots & \vdots\\
\beta_{n,1} & \beta_{n,2} & \cdots & \beta_{n,i-1} & \beta_{n,i} & \beta_{n,i+1} & \cdots & \beta_{n,n}
\end{vmatrix}
}.
$$

It remains to trade $$\beta$$ for $$\alpha$$ according to the bijection
we defined earlier, then swap the first column with the $$\ell^{\text{th}}$$
one if necessary.

If $$\ell = 1$$, we have nothing to do. Otherwise swaping the columns
multiplies both determinants by $$-1$$, hence the sign of
the ratio remains unchanged. We get

$$
x_i = (-1)^i
\frac{
\begin{vmatrix}
\alpha_{1,0} & \alpha_{1,1} & \alpha_{1,2} & \cdots & \alpha_{1,i-1} & \alpha_{1,i+1} & \cdots & \alpha_{1,n}\\
\alpha_{2,0} & \alpha_{2,1} & \alpha_{2,2} & \cdots & \alpha_{2,i-1} & \alpha_{2,i+1} & \cdots & \alpha_{2,n}\\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots\\
\alpha_{n,0} & \alpha_{n,1} & \alpha_{n,2} & \cdots & \alpha_{n,i-1} & \alpha_{n,i+1} & \cdots & \alpha_{n,n}
\end{vmatrix}
}
{
\begin{vmatrix}
\alpha_{1,1} & \alpha_{1,2} & \cdots & \alpha_{1,n}\\
\alpha_{2,1} & \alpha_{2,2} & \cdots & \alpha_{2,n}\\
\vdots & \vdots & \ddots & \vdots\\
\alpha_{n,1} & \alpha_{n,2} & \cdots & \alpha_{n,n}
\end{vmatrix}
}
$$

as claimed, QED.

