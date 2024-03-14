# Foundations of optimization 14

## Representative CLP Problems

**Standard form Conic Linear Programming (CLP) problem**

$$
\begin{aligned}
v_p^* =\inf & \ c\bullet x \\
\mathrm{s.t.} & \ a_i\bullet x=b_i\quad\mathrm{for~}i=1,...,m,\\
& x\succeq_K0.\end{aligned}
$$

> $x\succeq_K0$ means $x \in K$

- 如果 $K$ 是非负象限，那么该问题就是一个 LP 问题
- 如果 $K$ 是半正定矩阵锥，那么该问题就是 SDP 问题
- 如果 $K$ 是二阶锥，那么问题就是 SOCP (Second-Order Cone Programming)

**Linear Programming**

$$
\begin{aligned}
v_p^* =\inf & \ c\bullet x \\
\mathrm{s.t.} & \ a_i\bullet x=b_i\quad\mathrm{for~}i=1,...,m,\\
& x \in \mathbb{R}^n_+
\end{aligned}
$$

**Second-Order Cone Programming**

$$
\begin{aligned}
v_p^* =\inf & \ c\bullet x \\
\mathrm{s.t.} & \ a_i\bullet x=b_i\quad\mathrm{for~}i=1,...,m,\\
& x \in \mathcal{Q}^{n+1}
\end{aligned}
$$

The class of SOCPs includes the class of LPs as a special case.

**Semidefinite Programming**

$$
\begin{aligned}
v_p^* =\inf & \ C \bullet X \\
\mathrm{s.t.} & \ A_i\bullet X=b_i\quad\mathrm{for~}i=1,...,m,\\
& x \in \mathcal{S}^n_+
\end{aligned}
$$

The class of SPDs includes the class of SOCPs as a special case.

## CLP Duality

**Dual of CLP**

$$
\begin{aligned}
    v_d^* = \sup \  &b^T y \\
    \text{s.t. } & \sum_{i=1}^m y_i a_i + s = c \\
    & y \in \mathbb{R}^m, s \succeq_{K^*} 0
\end{aligned}
$$

> [!THEOREM|label:CLP Weak Duality]
> Let $x \in K$ be feasible for primal and $(y,s) \in \mathbb{R}^m \times K^* $ be feasible. Then $b^T y \leq c \bullet x$

Recall Farkas Lemma in LP:

- $a_i^Tx=b_i,\mathrm{~for~}i=1,...,m,x\in\mathbb{R}_+^n.$
- $\sum_{i=1}^my_ia_i\in\mathbb{R}_+^n,b^Ty<0.$

For two conic linear systems

- $a_i\bullet x=b_i,\mathrm{~for~}i=1,...,m,x\in K.$
- $\sum_{i=1}^my_ia_i\in K^*,b^Ty<0.$

> [!THEOREM|label:CLP Strong Duality]
> Suppose that either Primal or Dual is bounded and **strictly feasible**(Slater Condition). Then, given a feasible solution $\bar{x}$ to Primal and a feasible solution $(\bar{y},\bar{s})$ to Dual, the following are equivalent:
>
> - $\bar{x}$ and $(\bar{y},\bar{s})$ are optimal for Primal and Dual respectively
> - The duality gap is zero, $c \bullet \bar{x} = b^T y$
> - Complementary slackness, $\bar{x} \bullet \bar{s} =0$


