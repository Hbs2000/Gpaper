# Foundations of Optimization 9


## Standard forms

We can always represent a linear program as:

$$
\begin{aligned}\min \ &\mathrm{c^Tx}\\s.t. \ &\mathrm{Ax=b}\\&\mathrm{x\geq0}\end{aligned}
$$

The above formulation is called **standard form**

### Transfer to Standard form

$$
\begin{aligned}
\text{min } & 3x_1+2x_2-x_3+x_4  \\
\text{s.t. } & x_1+2x_2+x_3-x_4\leq5  \\
&-2x_1-4x_2+x_3+x_4\leq-1 \\
&x_{1}\geq0 \\
&x_2\leq0
\end{aligned}
$$

Standard Form:

$$
\begin{aligned}
\min \  & 3y_{1}-2y_{2}-y_{3}+y_{4}+y_{5}-y_{6} \\
s.t. \ &y_{1}-2y_{2}+y_{3}-y_{4}-y_{5}+y_{8}+y_{7}=5 \\
&-2y_{1}+4y_{2}+y_{3}-y_{4}+y_{3}-y_{8}+y_{8}=-1 \\
&y_{1},y_{2},\cdots y_{8}\geq0 \\
& y_1 = x_1\\
&y_2 = - x_2 \\
& y_3 - y_4 = x_3 \\
& y_5 - y_6 = x_4
\end{aligned}
$$

## Certificate of Infeasibility

**When is an LP feasible/infeasible?**

*When constraints of the LP can be represented by equalities* ($Ax = b$)

Consider the following linear program:

$$
\begin{aligned}
\text{max }& 8x_1+x_2+x_3  \\
\text{s.t. }& x_1+x_2+x_3=6  \\
&2x_1+3x_2+x_3=8 \\
&2x_1+x_2+3x_3=0
\end{aligned}
$$

The constraints are $Ax = b$ where

$$
A=\begin{pmatrix}1&1&1\\2&3&1\\2&1&3\end{pmatrix},\quad\mathrm{b}=\begin{pmatrix}6\\8\\0\end{pmatrix}
$$

By performing row operations on the matrix (**Gaussian elimination**), we see the LP is infeasible. The certificate of infeasibility is $y^T = (4,-1,-1)$

That is, there exists $y$, such that $y^T A = 0$ and $y^T b = 16 \neq 0$


## Certificate of Feasibility

Let $A$ be a $ m \times n$ matrix, and $b \in \mathbb{R}^m$. Then exactly one of the following statements holds:

(a) $\exist x \in \mathbb{R}^n, \text{ s.t. }, Ax = b$

(b) $\exist y \in \mathbb{R}^m, \text{ s.t. }, y^T A =0 \text{ and } y^T b \neq 0$

**How to check the feasibility for a standard form LP?**

### Farkas Lemma

Let $A$ be a $ m \times n$ matrix, and $b \in \mathbb{R}^m$. Then exactly one of the following statements holds:

(a) $\exist x \in \mathbb{R}^n, \text{ s.t. }, Ax = b, x\geq 0$

(b) $\exist y \in \mathbb{R}^m, \text{ s.t. }, y^T A \geq 0 \text{ and } y^T b < 0$

> [!NOTE|The difference between the two lemma]
> Farkas Lemma 是对于标准 LP 问题而言的，Gauss Lemma 并不要求 $x \geq 0$。


**Another form**

Let $A$ be a $ m \times n$ matrix, and $b \in \mathbb{R}^m$. Then exactly one of the following statements holds:

(a) $\exist x \in \mathbb{R}^n, \text{ s.t. }, Ax \leq b$

(b) $\exist y \in \mathbb{R}^m, \text{ s.t. }, y^T A =0,y\geq 0 \text{ and } y^T b < 0$



## Primal and Dual: Intuition

Consider the following optimization problem:

$$
\begin{aligned}
\text{min } & x_1+2x_2+4x_3  \\
\text{s.t. } &  x_1+x_2+2x_3=5  \\
&2x_1+x_2+3x_3=8 \\
&x_1,x_2,x_3\geq0
\end{aligned}
$$

To find an optimal solution, we try to find upper and lower bounds:

$$
\text{lower bound} ≤ \text{optimal solution} ≤ \text{upper bound}
$$

- Upper bounds: Try to guess $(2,1,1)^T,(3,2,0)^T...$
- Lower bounds: Multiply constraints by $(2,-1),(3,-1) ....$ 【get from duality problem】

**Primal**

$$
\begin{aligned}\alpha^* =  \min \ &c^Tx \\  \text{ s.t. }&A\mathrm{x}=\mathrm{b}\\ & x\geq0\end{aligned}
$$

**Dual**

$$
\begin{aligned}\beta^*=  \max & \ y^Tb\\  \text{ s.t.} & \ y^TA\leq c^T\end{aligned}
$$

**LP Weak Duality**

Let $x$ be a feasible solution to *PRIMAL*, $y$ be a feasible solution to DUAL. Then $\mathsf{c^{T}x\geq y^{T}b}.$ In particular, we have $\begin{aligned}\alpha^*\geq\beta^*\end{aligned}$.

- If $ \alpha^* = - \infty$, then $\beta^* = - \infty$, i.e. DUAL is infeasible
- If $\beta^* = + \infty$, then $ \alpha^* = + \infty$, i.e. PRIMAL is infeasible
- The dual of the dual is the primal

**LP Strong Duality**

If either PRIMAL or DUAL is feasible, then $\alpha^* = \beta^* $


> [!THEOREM|label:Complementary Slackness]
> Let $x$ and $y$ are feasible solutions to the Primal and Dual respectively. Then both $x$ and $y$ are optimal if and only if
$$
(\mathrm{y}^\mathsf{T}A-\mathrm{c}^\mathsf{T})\mathrm{x}=0.
$$
> 

> [!TIP|label:Proof]
> Zero duality gap
$$
(y^{T}A-c^{T})x=0\Longleftrightarrow y^{T}Ax-c^{T}x=0\Longleftrightarrow y^{T}b-c^{T}x=0
$$
> 


### Example

Consider the following linear program:

$$
\begin{aligned}
\text{min }& -6x_1-6x_2-4x_3  \\
\text{s.t. }& 4x_1+6x_2+2x_3+x_4=24  \\
&4x_1+4x_2+3x_3=20 \\
&2x_1+3x_2+x_3=8 \\
&x_1\geq0,x_2\geq0,x_3\geq0,x_4\geq0.
\end{aligned}
$$

Use the LP duality, check if

$$
x_1=2,x_2=0,x_3=4,x_4=8
$$

is an optimal solution.

根据 Complementary Slackness，得到 $y$，check if $y$ is feasible for dual problem

