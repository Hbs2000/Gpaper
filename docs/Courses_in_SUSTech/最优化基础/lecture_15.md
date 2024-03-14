# Foundations of optimization 15

**Standard form Conic Linear Programming (CLP) problem**

$$
\begin{aligned}
v_p^* =\inf & \ c\bullet x \\
\mathrm{s.t.} & \ a_i\bullet x=b_i\quad\mathrm{for~}i=1,...,m,\\
& x\succeq_K0.\end{aligned}
$$

**Dual of CLP**

$$
\begin{aligned}
    v_d^* = \sup \  &b^T y \\
    \text{s.t. } & \sum_{i=1}^m y_i a_i + s = c \\
    & y \in \mathbb{R}^m, s \succeq_{K^*} 0
\end{aligned}
$$

## CLP Strong Duality

> Farkas lemma 不适用对 CLP 问题带来的影响具体体现在哪

1. Suppose that Primal is bounded below and strictly feasible, then we have $v_p^* = v_d^*$. Moreover, there exists a feasible solution $(\bar{y},\bar{s})$ to Dual such that $b^T \bar{y} = v_d^* = v_p^*$

2. Suppose that Dual is bounded above and strictly feasible, then we have $v_p^* = v_d^*$. Moreover, there exists a feasible solution $\bar{x}$ to Primal such that $c \bullet \bar{x} = v_d^* = v_p^*$

3. Suppose that either Primal or Dual is bounded and strictly feasible. Then, given a feasible solution $\bar{x}$ to Primal and a feasible solution $\bar{y},\bar{s}$ to Dual, the following are equivalent:

    - $\bar{x}$ and $(\bar{y},\bar{s})$ are optimal for Primal and Dual, respectively.
    - The duality gap is zero: $c \bullet \bar{x} = b^T \bar{y} $
    - Complementary slackness $\bar{x} \bullet \bar{s} = 0$

## Quadratically Constrained Quadratic Optimization

> QCQR 转化成 SDP 求解。

$$
\begin{aligned}
    \text{min } & x^T C x \\ 
    \text{s.t. } & x^T A_i x \geq b_i, \text{ for } i = 1, \cdots m
\end{aligned}
$$

It can be solved by the **semidefinite relaxation** technique

$$
\begin{aligned}
    \text{min } & C \bullet X \\
    \text{s.t. } & A_i \bullet X \geq b_i,  \text{ for } i = 1, \cdots m \\
    & X \succeq 0,  \text{rank} (X) \leq 1
\end{aligned}
$$

By **dropping** the non-convex constraint $\text{rank}(X) \leq 1$, we obtain:

$$
\begin{aligned}
    \text{min } & C \bullet X \\
    \text{s.t. } & A_i \bullet X \geq b_i,  \text{ for } i = 1, \cdots m \\
    & X \succeq 0
\end{aligned}
$$

which is an SDP.

**Corollary**: The semidefinite relaxation is tight when **$ m \leq 2 $**
