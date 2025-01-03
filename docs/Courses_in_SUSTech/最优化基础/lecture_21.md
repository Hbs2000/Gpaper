# Foundations of optimization 21

## Combinatorial/Discrete Optimization

### Knapsack Problem

**Input**

- $n$ items, each item $i$ has cost $c_i \in \mathbb{Z}^+$ and value $v_i \in \mathbb{Z}^+$
- budget $B \in \mathbb{Z}^+$, assume $c_i \leq B$ for all $i$

**Output**

Find a subset $S$ of items whose cost $c(S) = \sum_{i \in S} c_i$ is less or equal to $B$, and whose value $v(S) = \sum_{i \in S}v_i $ is maximal

Write as the following integer program:

$$
\begin{aligned}
    \max \ & v^T x \\
    \text{s.t. } & v^T x \leq B \\
    & x_i \in \{ 0,1 \}
\end{aligned}
$$

Relax the integer constraints:

$$
\begin{aligned}
    \max \ & v^T x \\
    \text{s.t. } & c^T x \leq B \\
    & 0 \leq x_i \leq 1
\end{aligned}
$$

A simple modification can achieve $\frac{1}{2}$-approximation.

> [!THEOREM]
> Let $S^* = \argmax \{ v(S),v(a) \}$, where $S$ is the solution returned by Greedy Algorithm, $a$ is the element with highest density that is not in $S$. Then 
$$
v(S^*)\geq\frac{OPT}2
$$
> where $OPT$ denotes the value of an optimal solution

## Theory of Computation Complexity

The theory of computational complexity usually considers decision problems. 

> [!THEOREM|label:Definition]
> A decision problem is a function $Q:\{0,1\}^x\to\{ YES,NO\}.$ In other words, the input of a decision problem is a sequence $x$ of bits.

Any optimization problem can be reformulted as a decision problem.

> **KNAPSACK**: $Q(x)=$ does there exist a subset of the $n$ items of cost at most $B$ and value at least $V$?


### P and NP


**时间复杂度**： 时间复杂度并不是表示一个程序解决问题需要花多少时间，而是当问题规模扩大后，程序需要的时间长度增长得有多快。

对于高速处理数据的计算机来说，处理某一个特定数据的效率不能衡量一个程序的好坏，而应该看当这个数据的规模变大到数百倍后，程序运行时间是否跟着慢了数百倍，或者变慢了数万倍。不管数据有多大，程序处理花的时间始终是那么多的，我们就说这个程序很好，具有 $O(1)$ 的时间复杂度，也称常数级复杂度，数据规模变得有多大，花的时间也跟着变得有多长，这个程序的时间复杂度就是 $O(n)$，比如找 $n$ 个数中的最大值；而像冒泡排序、插入排序等，数据扩大2倍，时间变慢4倍的，属于 $O(n^2)$ 的复杂度。

> 此处需要考虑数量级，因此没有 $O(2n)$ 的复杂度，同样地，也没有 $O(n^3+n^2)$ 的复杂度。

复杂度通常有以下两种分类：

- $O(1),O(log(n)),O(n^a)$，这种被称之为多项式级的复杂度，因为其规模 $n$ 出现在底数的位置
- $O(a^n), O(n!)$，这种是非多项式级的，其复杂度计算机往往不能承受

通常当我们在解决一个问题时，所选算法都需要是多项式级的复杂度，因为非多项式级的复杂度所需时间太多，除非数据量非常小。

那么，会不会所有的问题都可以找到复杂度为多项式级的算法呢？答案是否定的，有些问题甚至根本不可能找到一个正确的算法来，这称之为不可解问题 (Undecidable Desicion Problem)。接下来会从这一点区分问题：

<div class = 'centerwords'>

Polynomial class
</div>

如果一个问题可以找到一个能在多项式的时间里解决它的算法，那么这个问题就属于 $P$ 类问题。


<div class = 'centerwords'>

Non-Polynomial class
</div>

**NP 问题不是非 P 问题**。NP 问题是指可以在多项式的时间里验证一个解的问题，或者说，可以在多项式时间里猜出一个解的问题。

例如求最短路径的问题。例如算一条单位长度小于 100 的路径，但是怎么算都算不出来，但是人品爆发，一猜就猜出来了一条。找一个解很难，但是验证一个解很简单，验证一个解只需要 $O(n)$ 的复杂度，只要把猜的路径加起来就可以了。

当然也有不是 NP 问题的问题，也就是猜到了解但是没用，因为不能够在多项式的时间里验证它。

之所以要定义 NP 问题，是因为 **通常只有 NP 问题才可能找到多项式算法**。如果一个问题连多项式地验证一个解都做不到，那么更不能指望存在一个解决它的多项式算法。

> KNAPSACK $\in$ NP

### The relationship

信息学中号称最难的问题，就是在讨论 NP 问题与 P 类问题之间的关系。

很显然，**所有的 P 类问题都是 NP 问题**。也就是说，能多项式地解决一个问题，必然能多项式地验证一个问题的解是否存在，既然正解都出来了，验证任意给定的解也自然不是问题。

那么是否所有的 NP 问题都是 P 类问题？也就是 NP = P。普遍来说，学者们认为 $P\neq NP$，也就是说，多数人相信**至少存在一个不可能有多项式级复杂度算法的 NP 问题**。这是因为，在研究 NP 问题的过程中找出了一类非常特殊的 NP 问题叫做 **NP-Complete** 问题 （以下简称 NPC 问题），正是因为 NPC 问题的存在，使得人们坚信 $P\neq NP$。

### Reducibility and NPC

**How to compare two problems and show that one is harder or simpler than the other?**

简单地说，一个问题 A 可以约化为问题 B 的含义既是：**可以用问题 B 的解法解决问题 A**。

> 例如，现在有两个问题，求解一元一次方程和求解一元二次方程，那么我们可以说，前者可以约化为后者，也就是说知道如何解一元二次方程一定知道如何解一元一次方程。

用时间复杂度来解释，就是 **B 的时间复杂度高于或等于 A 的时间复杂度**，也就是说，问题 A 不比问题 B 难。

约化的标准概念：如果能找到这样一个变化法则，对任意一个程序A的输入，都能按这个法则变换成程序B的输入，使两程序的输出相同，那么我们说，问题A可约化为问题B。当然，此处说的可约值得是多项式地可约，该约化的过程只有用多项式的时间完成才有意义。

> [!THEOREM|label:Reducibility]
> Let $Q$ and $R$ be two decision problems. $Q$ is poly-time reducible to $R$ is written as:
$$
Q \leq_P R
$$
> 

约化具有**传递性**：如果 A 可以约化为 B，B 可以约化为 C，那么 A 也可以约化为 C。

***那么约化有什么用呢？***

**当一个问题约化为另一个问题，时间复杂度增加了，问题的应用范围也增大了。通过对于某些问题的不断约化，我们能够不断寻找复杂度更高，但应用范围更广的算法，来代替复杂度虽然低，但只能应用于很小的一类问题的算法**。

那么，根据约化的传递性，有没有可能找到一个能够通吃所有 NP 问题的超级 NP 问题？**答案居然是肯定的**，那么也就是说，**存在这样一个 NP 问题，所有 NP 问题都可以约化为它，只要解决了这个问题，那么也解决了所有的 NP 问题**。这种问题的存在难以置信，并且更加不可思议的是，这种问题不只一个，它有很多个，它是一类问题。这就是传说中的 **NPC 问题**。

NPC 问题的定义非常简单，同时满足下面两个条件即可：

1. 它是一个 NP 问题
2. 所有的 NP 问题都可以约化为它

NPC 问题的存在使得整个 NP 问题的研究出现了飞跃式的发展。既然所有的 NP 问题都能约化成 NPC 问题，**那么只要任意一个 NPC 问题找到了一个多项式的算法，其对应的所有 NP 问题都被解决了**，那么只要给 NPC 问题找到了一个多项式算法，所有的 NP 问题都可以用该算法解决了，NP 也就等于 P 了。但是，**NPC 问题目前没有多项式的有效算法，只能用指数级甚至阶乘级复杂度的搜索**。

通过约化，证明一个问题是 NPC 问题也很简单。先证明其至少是一个 NP 问题，再证明其中一个已知的 NPC 问题能约化到它。目前有许多的 NPC 问题，正是因为这些问题的存在，使得 $P=NP$ 变得难以置信。

**NP-Hard**：NP-Hard 问题满足 NPC 定义的第二条，**但不满足第一条**。这种问题不列入研究范围，因为不是 NP 问题。若问题 A 不属于 NP 问题，已知某 NPC 问题可在多项式时间内转化为问题 A，则称 A 为 NP-Hard 问题。


## Submodular Function

A function $f:2^N \to \mathbb{R}$ with $f(\emptyset)=0$ is **submodular** if

$$
f(S\cup T)\leq f(S)+f(T)-f(S\cap T),\mathrm{~}S,T\subseteq N.
$$

**Marginal contribution**: For a function $f:2^N \to \mathbb{R}$ and a set $S \subseteq N $, the marginal contribution of $T \subseteq N$ to $S$ is:

$$
f_S(T)=f(T\cup S)-f(S).
$$

> [!THEOREM]
> A function $f:2^N \to \mathbb{R}$ is **submodular** iff 
$$
f_S(a)\geq f_T(a),S\subseteq T,\mathrm{~}a\in N\setminus T.
$$
> 次模函数描述的就是**边际效应递减**


### An algorithm for Submodular Maximization

For any submodualr function $f$, our goal is to 

$$
\max_{T:|T|\leq k}f(T)
$$

<div align='center'>

![](../image/20240110CV1.png)
</div>

For any monotone submodular function $f$, Algorithm 2 returns a set $S$ such that:

$$
f(S)\geq(1-\frac1e)\max_{T:|T|\leq k}f(T).
$$

**Lemma**: Let $S$ be the set selected by the greedy algorithm at some stage and let $a \in S$ be the element added to $S$ at this stage. Then

$$
f_S(a)\geq\frac1k[\max_{T:|T|\leq k}f(T)-f(S)].
$$

> It was proven in 1998 that unless $P=NP$, no polynomial time algorithm can obtian an approximation ratio better than $1 - 1/e$



