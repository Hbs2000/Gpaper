# Foundations of Optimization 8

## Linear programming

$$
\begin{array}{ll}\mathrm{minimize}&c^Tx\\\mathrm{subject~to}&a_i^Tx\leq b_i,\quad i=1,\ldots,m.\end{array}
$$

where the functions $f$ and $g_1,\cdots,g_m$ are all **linear**


## Basic definitions

**Hyperplane and halfspace**: Let $s\in\mathbb{R}^n\setminus\{0\}$ and $c \in \mathbb{R}$ be given. Then, the set of solutions to the linear equation $s^T x=c$, namely

$$
H=\{x\in\mathbb{R}^n:s^Tx=c\}
$$

is called a **hyperplane** in $\mathbb{R}^n$. A hyperplane divide $R^n$ into two  **halfspaces**, $H^- \text{ and } H^+$

A **polyhedron** is the intersection of a **finite** set of halfspaces. A bounded polyhedron is called a **polytope**.

> [!WARNING|label:Finite]
> Non-Polyhedrality of the Euclidean Ball

A polyhedron can be represented as

$$
P=\{x\in\mathbb{R}^n:a_i^Tx\leq b_i\mathrm{~for~}i=1,...,m\}
$$

## External elements of a Polyhedron

Let $\mathcal{P}\subset\mathbb{R}^n$ be a polyhedron and consider a point $\bar{x} \in P$. Let $I$ be the set of indices of constraints that are **active/binding** at $\bar{x}$, i.e. $I = \{i:a_i^T\bar{x}=b_i\}$. The following are equivalent:

1. There exist $n$ vectors in the set $\{a_i\in\mathbb{R}^n:i\in I\}$ that are linearly independent.

2. The point $\bar{x}$ is the unique solution to the following system of linear equations:

$$
a_i^Tx=b_i\mathrm{~for~i\in I}.
$$

Let $P\subset \mathbb{R}^n$ be a polyhedron and $x\in \mathbb{R}^n$ be arbitrary. The vector $x$ is called a **basic solution** if there are $n$ linearly independent active constraints at $x$. If in addition we have $x\in P$ then we say that $x$ is a **basic feasible solution**.

> basic solution can be not feasible to $P$ 

**Geometric view of basic feasible solution**

Let $P \subset \mathbb{R}^n$ be a polyhedron and $x\in P$ bearbitrary. The following are equivalent:

(a) $x$ is an extreme point

(b) $x$ is a basic feasible solution

we also refer $x$ as an **vertex**

Thus, we have **vertex = extreme point = basic feasible solution**

> [!TIP|label:Proof]
> Suppose $x\in P$ is **not** a basic feasible solution. Let $I = \{i:a_i^Tx=b_i\}$ 
>
> Then the family $I = \{i:a_i^Tx=b_i\}$ does not contain $n$ linearly independent vectors. Thus $\exist$ non-zero $d\in\mathbb{R}^n$, s.t. $a_i^Td=0 \ \forall i\in I.$ Let $\varepsilon > 0$
>
> Set $x_1 = x - \varepsilon d \text{ and } x_2 = x+ \varepsilon d$. For any $i \notin I$, we have $a_i^T x_1 = a_i^T x_2 = b_i $. For any $i \notin I$, we have $a_i x < b_i$ since $x \in P$
>
> Then for sufficiently small $\varepsilon$, we have $a_i^T x_1 <0, \ a_i^T x_1 <0 \text{ for } \forall i \notin I$.
>
> Hence, $x_1,x_2 \in P$ and $x = \frac{x_1 + x_2}{2} \Rightarrow$ x is **not an extreme point**
>
> Conversely, suppose $x \in P$ is not an extreme point. Let $x_1,x_2 \in P$, s.t. $x = \frac{x_1 + x_2}{2}$ and let $I = \{i:a_i^Tx=b_i\}$. Since $x_1,x_2 \in P$, we have $a^T_i x_1 \leq b_i $ and $a^T_i x_2 \leq b_i$ for $i = 1,2\cdots m \ \Longrightarrow a^T_i x_1 = a^T_i x_2 = a^T_i x = b_i \text{ for } \forall i \in I$.
>
> This implies that the system of linear equations $a^T_i z = b_i \text{ for } \forall i \in I $ has more than one solutions in $\mathbb{R}^n \ \Longrightarrow x$ is not a feasible solution. 
>

**Not every polyhedron has a vertex**. Consider a halfspace in **R^2**. So how to characterize polyhedra that have vertices.

Let $P \subset \mathbb{R}^n$ be a polyhedron and $x \in P$ be arbitrary. The following are equivalent.

(a) $P$ has at least one vertex

(b) There exists $n$ linear independent constraints.

(c) $P$ does not **contain a line**

> [!NOTE|label:contain a line]
> A polyhedron $P \subset \mathbb{R}^n$ contains a $line$ if there exists a point $x\in P$ and a vector $d \in \mathbb{R}^n \setminus \{0\}$ such that $x + \alpha d \in O$ for all $\alpha \in \mathbb{R}$

## Existence of Optimal Solutions to Linear Programs

Let $P=\{x\in\mathbb{R}^n:a_i^Tx\leq b_i\mathrm{~for~}i=1,...,m\}$ be a non-empty polyhedron and $h \in \mathbb{R}^n$ be a given vector. Consider the LP

$$
\underset{x\in P}{\text{min}} \ h^T x
$$

**When LP has an optimal solution**

Consider the LP. Suppose that $P$ has at least one vertex. Then, **either the optimal value is** $-\infty$, **or there exists a vertex that is optimal**.

> [!TIP|label:Proof]
>
> We say $x\in P$ has rank $k$ if there are exactly $k$ linearly independent active constraints at $x$.

We can always transform the above LP into an equivalent LP whose feasible set has at least one vertex. To see this, consider the polyhedron $P'$ given by

$$
\min_{x\in P}h^Tx=\min_{(x^+,x^-,s)\in P^{\prime}}h^T(x^+-x^-).
$$

where

$$
\begin{aligned}P^{\prime}=\{(x^+,x^-,s)\in\mathbb{R}^n\times\mathbb{R}^n\times\mathbb{R}^m:a_i^T(x^+-x^-)+s_i=b_i\\\mathrm{for~}i=1,...,m;\mathrm{~}x^+,x^-,s\geq0\}.\end{aligned}
$$

The $P'$ is intersection of $m$ halfspaces, hence it always has at least one vertex.












