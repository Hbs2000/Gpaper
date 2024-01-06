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


***There always exists an mixed strategy equilibrium in two players zero-sum game.***

## Cooperative Games

What if the game is not zero-sum? John Nash defined a solution called **Nash equilibrium** in 1950s













