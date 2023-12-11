# Foundations of Optimization 7

## Convexity-Preserving Transformations

(a) **Non-negative Combinations**: Let $f_1,...,f_m:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$ be convex functions. Then for any $\alpha_1,...,\alpha_m\geq0$ , the function $f$ defined by

$$
f(x)=\sum_{i=1}^m\alpha_if_i(x)
$$

is convex

(b) **Pointwise Supermum**: Let $I$ be an index set and $\{f_i\}_{i\in I}$ be a family of convex function. Define the pointwise superemum $f$ by

$$
f(x)=\sup_{i\in I}f_i(x).
$$

Then $f$ is convex.


(c) **Affine composition**: Let $\mathbf{g}:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$ be a convex functions and $A:\mathbb{R}^m\to\mathbb{R}^n$ be an affine mapping.Then the function $\mathbf{g}:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$ defined by $f(x) = g(A(x)) $ is convex.


(d) **Composition with an Increasing Convex Function**: Let $g:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$ and $h:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$ be convex functions that are not identically $+\infty$. Suppose $h$ is increasing on $dom(h)$. Then the function defined by $f(x) = h(g(x))$ is convex.

(e) **Restriction on Lines**: Given a function $f:\mathbb{R}^n\to\mathbb{R}\cup\{+\infty\}$, a point $x_0 \in \mathbb{R}^n$, and a direction $h\in \mathbb{R}^n$, define the function $f_{x_0,h}:\mathbb{R}\to\mathbb{R}\cup\{+\infty\}$ by $f_{x_0,h}(t)=f(x_0+th)$. Then the function $f$ is convex iff the function $f_{x_0,h}(t)$ is convex for any $x_0, h \in \mathbb{R}^n$


## Differentiable Convex Functions

The **gradient** of a function $f: \mathbb{R}^n \to \mathbb{R}$ at point $x\in \mathbb{R}^n$ is defined as:

$$
\nabla f(x)=[\frac{\partial f(x)}{\partial x_1},...,\frac{\partial f(x)}{\partial x_n}]^T
$$

**First-order Taylor expansion**: If $f: \mathbb{R}^n \to \mathbb{R}$ differentiable at point $\bar{x} \in \mathbb{R}^n$, then for any $x\in \mathbb{R}^n$ we have

$$
f(x)=f(\bar{x})+\nabla f(\bar{x})^T(x-\bar{x})+o(||x-\bar{x}||)
$$

方向导数与梯度的联系：

**directional derivatives**: Let $f:\mathbb{R}^n \to \mathbb{R}$ be a function differentiable at point $x\in \mathbb{R}^n$, consider a direction $d\in \mathbb{R}^n$ with $||d|| = 1$. We define the derivative of $f$ at $x$ in direction $d$ as

$$
f^{\prime}(x,d)=\lim_{\lambda\to0}\frac{f(x+\lambda d)-f(x)}\lambda 
$$

Let $f: S \to \mathbb{R}$ and $S$ be a convex subset of $\mathbb{R}^n$. Then $f$ is convex on $S$ iff for any $x,y \in S$, we have

$$
f(y)\geq f(x)+\nabla f(x)^T(y-x).
$$

> [!NOTE|label:Relationship between gradient and directional derivatives]
> The directional derivative is a scalar, equals **gradient** $\times$ **unit vector**
>
> The directional derivative of a function in a given direction is **the rate at which the function changes as you move in that direction.**
>
> Gradient points in the direction of the greatest rate of increase of the function.

**Second-order Taylor expansion**: if $f: \mathbb{R}^n \to \mathbb{R}$ is twice differentiable at point $\bar{x} \in \mathbb{R}^n$, then for any $x\in \mathbb{R}^n$ we have:

$$
f(x)=f(\bar{x})+\nabla f(\bar{x})^T(x-\bar{x})+\frac12(x-\bar{x})^TH_f(\bar{x})(x-\bar{x}) + o(||x-\bar{x}||)
$$

$f$ is convex on $S$ iff $H_f(x)$ is positive semi-definite for any $x\in S$


