# Foundations of optimization 11

## Zero-Sum Game

- Two Players
- Player 1 has $m$ possible choices
- Player 2 has $n$ possible choices
- When player 1 choose $i$-th move and player 2 choose $j$-th move, then player 1 has to pays $A_{i,j}$ to player 2


**Pure strategy** equilibrium may not exists: 

$$
\min_i\max_jA_{ij}\neq\max_j\min_iA_{ij}
$$

> in Rock-Paper-Scissors, there is no pure strategy equilibrium.

Where pure strategy equilibria do not exist, **Mixed Strategy Equilibrium** becomes particularly relevant.


**Mixed strategy**: a distribution of moves

- Player 1’s distribution is $x\in \mathbb{R}^m$ with $x \geq 0 \text{ and } \sum_ix_i=1$
- Player 2’s distribution is $y\in \mathbb{R}^n$ with $y \geq 0 \text{ and } \sum_j y_j=1$
- The expected payoff from player 1 to player 2 is $\sum_{ij}x_iA_{ij}y_j=\mathrm{x}^\mathsf{T}A\mathrm{y}$

> [!THEOREM|label:Mixed Strategy Equilibrium]
> $ (\mathrm{x}^*,\mathrm{y}^*) $ is a mixed equilibrium iff
>
> 1. $\mathrm{x^*}^\mathsf{T}A\mathrm{y^*}\leq\mathrm{x^T}A\mathrm{y^*}$ for all player 1's distribution $x$
>
> 2. $\mathrm{x^{*T}}A\mathrm{y^*}\geq\mathrm{x^{*T}}A\mathrm{y}$ for all player 2's distribution $y$

We have:

$$
\min_{\mathrm{x}}\max_{\mathrm{y}}\mathrm{x}^{\mathrm{T}}A\mathrm{y}=\max_{\mathrm{y}}\min_{\mathrm{x}}\mathrm{x}^{\mathrm{T}}A\mathrm{y}
$$


> [!THEOREM|label:Minimax theorem]
> Von Neumann (1930s): ***There always exists an mixed strategy equilibrium in two players zero-sum game.***

## Cooperative Games

What if the game is not zero-sum? John Nash defined a solution called **Nash equilibrium** in 1950s

> In zero-sum games, the minimax solution is the same as the Nash equilibrium

合作博弈要解决的两个问题：

1. 如何构建 Coalition 
2. 如何分配收益

- a set of $\mathcal{N}=\{1,...,n\}$ of $n$ players
- $v:2^{\mathcal{N}}\to\mathbb{R}_+$ is the **value function**, i.e. for $S \subset \mathcal{N}$, the value of $v(S)$ is the worth of coalition $S$
- an allocation vector $x \in \mathbb{R}^n_+$, where $x_i \geq 0$ represents the payoff to player $i$
- an allocation $x$ is the **core** if 

$$
\begin{aligned}\sum_{i=1}^nx_i=&v(\mathcal{N}),\\\sum_{i\in\mathcal{S}}x_i\geq&v(\mathcal{S}),\text{ for all }S\subset\mathcal{N}.\end{aligned}
$$

core 的含义为：所有成员组成大联盟 $\mathcal{N}$，大联盟中任意几个成员收益累加，都要大于他们单独形成小联盟的收益，因此保证了不会有人背叛大联盟。

如何分配收益？Sharply value 告诉我们：按照联盟中成员的边际贡献的比例来分配收益。

对于一些 games 来说，core 可能是空的，可以通过以下定理来找出具有非空 core 的核。

> [!THEOREM|label:Theorem (Bondareva-Shapley)]
> The cooperative game $\mathcal{N,v}$ has a non-empty core if the following **balancedness condition** is satisfied: For any set of weights $\{y_S\}_S$ such that $y_S \geq 0$ and $\sum_{S:i\in\mathcal{S}}y_S=1$ for $i=1,...,n$, we have 
$$
\sum_S y_S v(S)\leq v(\mathcal{N}).
$$
> 

## Vextex Cover

**Vertex Cover Problem:** given an undirected graph $G = (V, E)$, where each vertex $v$ has an associated cost $c_v$ . We want to find a subset $S ⊂ V$ with minimal cost such that for every edge $e$, at least one of the endpoints belongs to $S$

This problem can be formulated as an integer problem:

$$
\begin{aligned}v^*=\min & \sum_{v\in V} c_vx_v\\
\mathrm{s.t~} & x_u+x_v\geq1 & \forall e=(u,v)\in E\\
&x_v\in\{0,1\} & \forall v\in V\end{aligned}
$$

> 包括所有顶点的，成本最小的连接方式

**The LP relaxation:**

$$
\begin{aligned}
v^*=\min &\sum_{v\in V}c_vx_v \\
\text{s.t }& x_u+x_v\geq1\quad\forall e=(u,v)\in E  \\
&0\leq x_v\leq1\quad\forall v\in V
\end{aligned}
$$

**Lemma 1**: Let $P$ be the feasible region of the relaxed problem. Suppose $x$ is an extreme point of $P$. Then we have $x_v\in\{0,\frac12,1\}$

An algorithm $\mathcal{A}$ is an $\alpha$−**approximation algorithm** for a minimization problem $\mathcal{P}$ if it delivers a solution whose objective value is at most $\alpha$ times the optimal value.

**Corollary 1**: We can find a 2-approximation algorithm for the minimum-cost
vertex cover problem.

**Corollary 2**: Given a $k$-coloring of a graph $G$, we can find a vertex cover which is a $2 - \frac{2}{k}$ approximation.
