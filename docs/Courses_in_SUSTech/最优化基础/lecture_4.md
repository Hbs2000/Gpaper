# Foundations of Optimization 4



## Projection theorem

**Projection Theorem I**

Let $S\subset\mathbb{R}^n$ be non-empty, closed, and convex. Then, for every $x \in \mathbb{R}^n$, there exists a unique point $z^* \in S$ that is closest (in the Euclidean norm) to x.

We refer the point $Z^*$ as the projection of $x$ on $S$, and denote it by:

$$
\Pi_S(x)=\mathrm{argmin}_{z\in S} \ ||z-x||_2^2
$$



**Projection Theorem II**

Let $S\subset\mathbb{R}^n$ be non-empty, closed, and convex. Given any $x \in \mathbb{R}^n $, we have $z^*=\Pi_S(x)\mathrm{~iff~}z^*\in S\mathrm{~and~}(z-z^*)^T(x-z^*)\leq0$ for all $z \in S$

