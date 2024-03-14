# Foundations of optimization 17

## Optimality Conditions for LP

**Primal**

$$
\begin{aligned}
    \min \ & c^Tx \\
    \text{s.t. } & Ax =b \\
    & x\geq 0
\end{aligned}
$$

**Dual**

$$
\begin{aligned}
    \max \ & y^T b \\
    \text{s.t. } & A^T y + s =c \\
    & s \geq 0
\end{aligned}
$$

$x^*$ and $(y^*,s^*)$ are optimal for Primal and Dual iff they satisfy **Optimality conditions**.

**Proposition** :Suppose that $f: \mathbb{R}^n \rightarrow \mathbb{R}$ is continuously differentiable at $\bar{x} \in \mathbb{R}^n$. If there exists a $d \in \mathbb{R}^n$ such that $\nabla f(\bar{x})^T d <0$, then there exists an $\alpha_0 > 0$ such that $f(\bar{x}+\alpha d) <f(\bar{x})$ for all $\alpha \in (0,\alpha_0)$. In other words, $d$ is a descent direction of $f$ at $\bar{x}$.

> [!NOTE|label:First Order Necessary Condition for Unconstrained Optimization]
> Suppose that $f: \mathbb{R}^n \rightarrow \mathbb{R}$ is continuously differentiable at $ \bar{x} \in \mathbb{R}^n $, if $\bar{x}$ is a local minimum, then we have $\nabla f(\bar{x}) = 0$.

If $f$ is convex, then the necessary condition is also **sufficient**.

**Proposition**: Let $S \subseteq \mathbb{R}^n $ be an open convex set. Suppose that $f: \mathbb{R}^n \rightarrow \mathbb{R}$ is convex on $S$ and continuously differentiable at $\bar{x} \in S$. Then, $\bar{x}$ is a **global minimum** in $S$ iff $\nabla f(\bar{x}) = 0$

> [!NOTE|label:Second Order Sufficient Condition for Unconstrained Optimization]
> Suppose that $f: \mathbb{R}^n \rightarrow \mathbb{R}$ is continuously differentiable at $ \bar{x} \in \mathbb{R}^n $. If $\nabla f(\bar{x}) = 0$ and $\nabla^2 f(\bar{x})$ is positive definite, then $\bar{x}$ is a local minimum.

