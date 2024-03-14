# Foundations of optimization 13

## Conic Linear Programming

**Standard form Conic Linear Programming (CLP) problem**

$$
\begin{aligned}
v_p^* =\inf & \ c\bullet x \\
\mathrm{s.t.} & \ a_i\bullet x=b_i\quad\mathrm{for~}i=1,...,m,\\
& x\succeq_K0.\end{aligned}
$$

> $x\succeq_K0$ means $x \in K$

**Dual of CLP**

$$
\begin{aligned}
    v_d^* = \sup \  &b^T y \\
    \text{s.t. } & \sum_{i=1}^m y_i a_i + s = c \\
    & y \in \mathbb{R}^m, s \succeq_{K^*} 0
\end{aligned}
$$



## Dual Cone

The **dual cone** of the cone $K$ is 

$$
K^*=\{w\in E:x\bullet w\geq0\text{ for all }x\in K\}.
$$

Let $ 0 \in K \subset E$ be a non-empty set. Then the following holds:

- The set $K^*$ is a **closed convex cone**
- If $K$ is a closed convex cone, we have $(K^*)^* =K$
- If $K$ has a non-empty interior, then $K^*$ is pointed
- If $K$ is a closed pointed cone, then $K^*$ has a non-empty interior

**Corollary**: Let $K \subset E$ be a closed pointed cone with non-empty interior. Then the dual cone $K^* \subset E$ is also a closed pointed cone with non-empty interior.



