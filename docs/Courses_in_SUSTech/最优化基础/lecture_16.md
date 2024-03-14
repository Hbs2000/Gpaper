# Foundations of optimization 16

## Approximation Algorithm for Maximum Cut

最大割问题是 NP-Complete 问题。给定一张图，求一种分割方法，将所有顶点 (Vertex) 分为两群，同时使得被切断的边数量最大。当每条边都有权重的时候，那么要保证最后切掉的边权重之和最大。

**Input:**

- an undirected graph $G = (V,E)$
- weight fucntion $w: E \rightarrow \mathbb{R}_+$

**Output:**

- a set $S \subset V$ such that the weight of the cut $(S,V \backslash S)$, i.e.

$$
w(S,V\backslash S)=\sum_{i\in S,j\in V\backslash S}w_{ij}
$$

is maximized.

Use SDP, it is possible to design a 0.878-approximation algorithm for the problem.

Let $n = |V|$, the MAX-CUT can be formulated as an integer quadratic program:

$$
\begin{aligned}
    v^*=\max & \frac12\sum_{(i,j)\in E}w_{ij}(1-x_ix_j) \\
    \text{s.t. } & x_i^2=1\quad\mathrm{for~}i=1,...,n.
\end{aligned}
$$

which can be rewritten as

$$
\begin{aligned}
    v^*=\max & \frac12\sum_{(i,j)\in E}w_{ij}(1-x_ix_j) \\
    \text{s.t. } &  \text{diag}(X) = e \\
    & X = xx^T
\end{aligned}
$$

Then **drop** the non-convex rank constraint, we derive the relaxation:

$$
\begin{aligned}
    v^*=\max & \frac12\sum_{(i,j)\in E}w_{ij}(1-x_ix_j) \\
    \text{s.t. } &  \text{diag}(X) = e \\
    & X \succeq 0
\end{aligned}
$$

Suppose $X^*$ is an optimal solution to above. We can obtain a feasible solution to MAX-CUT via **randomized rounding**.

> [!NOTE|label:Randomized rounding]
> 1. Compute the Cholesky decomposition $X^* = U^TU$, where $u \in \mathbb{R}^{n\times n}$. Let $u_i$ be the $i$-th column of $U$
> 2. Let $r \in \mathbb{R}^n$ be a vector uniformly distributed on the unit sphere $S^{n-1}=\{x\in\mathbb{R}^n:||x||_2=1\}.$
> 3. Set $x'_i = \mathrm{sgn}(u_i^T r)$ for $i=1,\cdots n$, where
$$
\mathrm{sgn}(z)=\begin{cases}1&\quad\mathrm{if~}z\geq0,\\-1&\quad\text{otherwise.}&\end{cases}
$$
> 

Let $u,v \in S^{n-1}$, and let $r$ be a vector uniformly distributed in $S^{n-1}$. Then we have 

$$
Pr[sgn(u^Tr)\neq sgn(v^Tr)]=\frac1\pi\arccos(u^Tv).
$$

Futhermore, for any $z \in [-1,1]$, we have 

$$
\frac1\pi\arccos(z)\geq\alpha\cdot\frac12(1-z)>0.878\cdot\frac12(1-z)
$$

> 这是什么意思，二者不相等的概率大于 $0.878\cdot\frac12(1-z)$ ?

**Corollary**: Given an MAX-CUT problem and an optimal solution to the
relaxed problem, the randomized rounding procedure will produce a $cut(S, V \backslash S)$ whose expected objective value satisfies $w(S, V \backslash S) \geq 0.878 V^*$


