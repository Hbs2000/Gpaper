# Foundations of Optimization

## Operations that Preserve Convexity

### Affine function 

$\mathbb{R}^n\to\mathbb{R}^m$ is affine if $A(x)=A_0x+y_0$ for some $A_0\in\mathbb{R}^{m\times n},y_0\in\mathbb{R}^m$

**Proposition**:

- Let $A:\mathbb{R}^n\to\mathbb{R}^m$ is affine and $S\subset \mathbb{R}^n$ be a convex set, then the image $A(S)=\{A(x)\in\mathbb{R}^m|x\in S\}$ is convex.

- Conversely, if $T\subset\mathbb{R}^m$ is a convex set, then the inverse image $A^{-1}(T)=\{x\in\mathbb{R}^n:A(x)\in T\}$ is convex.


> [!NOTE|label:Example]
> Convexity of Ellopsoid $E(x_c,Q)=\{x\in\mathbb{R}^n:(x-x_c)^TQ(x-x_c)\leq1\}$
> 
> define an affine Mapping $A(x)=Q^{-{1\over2}}x+x_c$
>
> Let $x\in B(0,1) $, then 
$$
(A(x)-x_{c})^{T}Q(A(x)-x_{c})=x^{T}Q^{-\frac{1}{2}}Q^{-\frac{1}{2}}x=x^{T}x\leq1
$$
> still is ball and convex
>
> conversely, Let $x\in E(x_c,Q) $, consider $A^{-1}(x)=Q^{\frac{1}{2}}(x-x_{i})=y$:
$$
(A^{-1}(x))^T A^{-1}(x) = (x-x_c)^TQ^{\frac{1}{2}}Q^{\frac{1}{2}}(x-x_c) \leq 1
$$
> still convex

### Perspective function

$P:\mathbb{R}^n\times\mathbb{R}_{++}\to\mathbb{R}^n$ such that $P(x,t)=\frac xt$.

**Proposition**:

- Let $P:\mathbb{R}^n\times\mathbb{R}_{++}\to\mathbb{R}^n$ be the perspective function and $S\subset\mathbb{R}^n\times\mathbb{R}_{++}$ be a convex set. Then the image $P(S)=\{x/t\in\mathbb{R}^n:(x,t)\in S\}$ is convex

- Conversely, if $T\subset \mathbb{R}^n$ is a convex set, then the inverse image $P^{-1}(T)=\{(x,t)\in\mathbb{R}^n\times\mathbb{R}_{++}:x/t\in T\}$ is convex.


> [!TIP|label:Proof]
> For any $x_{1}=(\overline{x}_{1},t_{1})\in R^{n}\times R_{++},\ x_{2}=(\overline{x}_{2},t_{2})\in R^{n}\times R_{+}+,\alpha\in[0,1]$
>
> we have:
$$\begin{aligned}
P\Big(\alpha x_{1}+(i-\alpha)x_{2}\Big) &=\frac{\alpha\overline{x}_{1}+(i-\alpha)\overline{x}_{2}}{\alpha t_{1}+(j-\alpha)t_{2}}. \\
&= \frac{\alpha t_{1}}{\alpha t_{1}+(1-\alpha)t_{2}}\cdot\frac{\overline{x}_{1}}{t_{1}}+\frac{(1-\alpha)t_{2}}{\alpha t_{1}+(1-\alpha)t_{2}}\cdot\frac{\overline{x}_{2}}{t_{2}} \\
&= \beta\cdot P(x_1)+(1-\beta)\cdot P(x_2)
\end{aligned}$$
> Thus, $P([x_{1},x_{2}])=[P(x_{1}),P(x_{2})]$


## Extremal Elements of a Convex Set

### Caratheodory’s Theorem

Let $S\subset \mathbb{R}^n $ be arbitrary. Then, any $x\in\mathrm{conv}(S)$ can be represented as a convex combination of at most $n+1$ points in $S$.

> 之所以是n+1，是因为用到了在n维空间中，最多存在n个线性无关的向量，因此n+1个向量必定线性相关。


> [!TIP|label:Proof]
> consider an arbitrary combination $x=\sum_{i=1}^{k}\alpha_{i}x_{i}\quad\mathrm{with}\quad x_{i},\cdots x_{k} \in S,\quad k\geq n+2$ 
>
> we want to show one of the $\alpha_i$ can be set to $0$.
>
> $\{x_{2}-x_{1},x_{3}-x_{1},\cdots x_{k}-x_{1}\}$ must be linearly dependetn in $R^n$
>
> $\exist \ \beta_{1},\cdots\beta_{k}\in R$ not all zero, s.t. $\sum_{i=1}^{k}\beta_{i}x_{i}=0\quad\mathrm{and} \quad \sum_{i=1}^{k}\beta_{i}=0$
>
> Let $t^{*}=\min_{j:\beta_{j}>0}\frac{\alpha_{j}}{\beta_{j}} = \max\{t\geq0:\alpha_{i}-t\beta_{i}\geq0,\text{for} \ \forall i\}$ and $\alpha_{i}^{\prime}=\alpha_{i}-t^{\star}\cdot\beta_{i}$
>
> Then we can verify that 
$$
x=\sum_{i=1}^{k}\alpha_{i}^{\prime}x_{i},\ \sum_{i=1}^{k}\alpha_{i}^{\prime}=1,\ \alpha_{i}^{\prime}\geq0,\left|{i:\alpha_{i}^{\prime}>0} \right| \leq k-1.
$$
> 
> The process can be repeated until there are only at most $n+1$ non-zero coefficient.
> 




#### Extreme point <!-- {docsify-ignore} -->

Let $S\subset\mathbb{R}^n$ be non-empty and convex. We say that $x\in\mathbb{R}^n$ is an extreme point of $S$ if $x \in S$ and there do not exist two different point $x_1,x_2 \in S$ such that $x=\frac12(x_1+x_2).$ 【例如圆的表面，三角形的顶点】




### Minkowski’s Theorem

Let $S \subset R^n $ be compact and convex. Then, $S$ is the convex hull of its extreme points.

> Compact: a subset is compact if and only if it is closed and bounded.

#### Extreme Faces <!-- {docsify-ignore} -->

Let $S \subset R^n $ be non-empty and convex. We say a non-empty convex set $F \subset R^n $ is a **face** of $S$ if $F \subset R^n $ and there do not exist two points $x_1,x_2\in S$ such that **(1)** $x_1\in S\backslash F\mathrm{~or~}x_2\in S\backslash F$, **(2)** $\frac12(x_1+x_2)\in F$

类似于三角体的每一个边或面，在去除这一个边后，其他所有的点不能用于表示这一条边上的点，因此该边称之为face。

**Proposition**：

(a) If $S'$ is a convex subset of $S$ and $x \in S'$ is an extreme point of $S$, then $x$ is an extreme point of $S'$

(b) If $F \subset S$ is a face of $S$, then any extreme point of $F$ is an extreme point of $S$.


## Topological Properties





## Projection onto Closed Convex Sets



