# Foundations of optimization 18 and 19

## Lagrangian Duals

一个原始最优化问题如下：

$$
\begin{array}{rl} \underset{x}{\min} &f_0(x)\\s.t.&f_i(x)\leq0,i=1,2,\ldots,m\\&h_j(x)=0,j=1,2,\ldots,p\end{array}
$$

则原问题的拉格朗日函数为

$$
L(x,\lambda,v)=f_0(x)+\sum_{i=1}^m\lambda_if_i(x)+\sum_{j=1}^pv_jh_j(x)
$$

对于该拉格朗日函数关于 $x$ 取下确界，得到拉格朗日对偶函数（简称对偶函数）：

$$
g(\lambda,v)=\inf_xL(x,\lambda,v)
$$

> [!NOTE|label:Dual problem]
> 对偶函数具有如下两条重要性质：
> 1. *对偶函数一定是 concave 函数，其凹性与原目标函数和约束函数凹凸与否无关*
> 
> $L(x,\lambda,v)$ 可以看作是一个无限的函数集，这个函数集中每个元素是 $L(x_i,\lambda,v)$，$x$ 取遍其在定义域上的所有值得到不同的 $x_i$。针对不同的 $x_i$，$L(x_i,\lambda,v)$ 的表达式不一样，由于这个表达式是只关于 $\lambda$ 和 $v$ 的，故用 $g_i(\lambda,v)$ 来表示，所以有
$$
g(\lambda,v)=\inf\{g_1(\lambda,v),g_2(\lambda,v),\ldots,g_\infty(\lambda,v)\}
$$
> 当把 $L$ 看成是关于 $\lambda$ 或 $v$ 的函数时，关于 $x$ 的项可理解为常数，因此 $L$ 是一个仿射函数，而对仿射函数取下确界，得到的函数就是 concave 函数。
>
> 2. 对 $\forall \lambda \geq 0, \forall v$，如果原问题最优解对应的目标函数值为 $p^*$，则有 $g(\lambda,v) \leq p^*$
>
> 结合 $f_i(x) \leq 0, h_j(x) = 0$，易得：
$$
L(x^*,\lambda,v)=f_0(x^*)+\sum_{i=1}^m\lambda_if_i(x^*)+\sum_{j=1}^pv_jh_j(x^*)\leq f_0(x^*)=p^*
$$
> 

根据对偶问题的性质2，其实也就是在说，对偶问题 $g(\lambda,v)$ 是原问题最优值 $p^*$ 的一个下界，那么最好的下界就是最大化对偶函数，因此构造原问题的对偶问题：

$$
\begin{array}{cc}\underset{\lambda,v}{\max}&g(\lambda,u)\\s.t.&\lambda\geq0\end{array}
$$

因为对偶函数是 concave 的，因此拉格朗日对偶问题一定是凸优化问题，对应的最优解为 $\lambda^*,v^*$，对应的最优值为 $d^*$，则总有 $d^* \leq p^*$：

1. 当 $d^* \leq p^*$，称为弱对偶 （weak duality）
2. 当 $d^* = p^*$，称为强对偶 （strong duality）
3. 将 $p^* - d^*$ 称为对偶间隙 （duality gap）

当解存在时，**弱对偶总是成立的**。而当满足强对偶时，可以通过求解对偶问题来得到原始问题的解。那么什么时候强对偶才成立呢？

## Slater's condition 

在原问题是 convex 的情况下，若 $\exists x\in relint(D)$，使得约束条件满足：

$$
f_i(x)<0,h_j(x)=0\quad i=1,2...,m;j=1,2,...,p
$$

则强对偶成立。

Slater 条件是一个充分不必要条件，即满足 Slater 条件，那么一定有强对偶，不满足 Slater 条件，强对偶也可能成立。


## Karush-Kuhn-Tucker（KKT）Conditions

当满足强对偶（zero duality gap），且 $L$ 对 $x$ 可微的前提下，设 $x^*,\lambda^*,v^*$ 分别是原问题和对偶问题的最优解，则以下条件称之为 KKT 条件：


$$
\begin{equation}
    \begin{aligned}
    f_i(x^{\star}) &\leq  0, \quad i=1, \ldots,m \\
    h_i(x^{\star}) &=0,\quad i=1,\ldots,p  \\
    \lambda_i^\star &\succeq0,\quad i=1,\ldots,m \\
    \lambda_i^\star f_i(x^\star)& =0,\quad i=1,\ldots,m  \\
    \nabla f_0(x^\star)+\sum_{i=1}^m\lambda_i^\star\nabla f_i(x^\star)+\sum_{i=1}^p\nu_i^\star\nabla h_i(x^\star)&=0.
    \end{aligned}
\end{equation}
$$

1. 等式1，2为原问题可行性（primal feasibility，即原问题的最优解必然满足原问题的约束条件）
2. 等式3为对偶问题可行性（dual feasibility，同理）
3. 等式4为互补松弛条件（complementary slackness），意为当 $\lambda_i^* >0,f_i(x^*)=0$，当 $f_i(x^*) <0,\lambda_i^*=0$

> [!TIP|label:Complementary slackness]
> 根据 zero duality gap，有：
$$
\begin{aligned}
f_{0}\left(x^{*}\right)& =g(\lambda^{*},v^{*})  \\
&=\inf_x\{f_0(x)+\sum_{i=1}^m\lambda_i^*f_i(x)+\sum_{j=1}^pv_j^*h_j(x)\} \\
&\leq f_0(x^*)+\sum_{i=1}^m\lambda_i^*f_i(x^*)+\sum_{j=1}^pv_j^*h_j(x^*)\\&\leq f_0(x^*)
\end{aligned}
$$
>
> 观察上式易知 $\leq$ 只能取 $=$，因此 $\sum_{i=1}^m\lambda_i^*f_i(x^*) =0$，又因为对于每一项都有 $\lambda_i^*f_i(x^*)\leq0$，因此 $\lambda_i^*f_i(x^*)=0$

4. 等式5代表 $L(x,\lambda^{\star},\nu^{\star})$ 在 $x=x^*$ 处的梯度为零

对于一般的原问题，KKT 条件是 $x^*,\lambda^*,v^*$ 为最优解的**必要条件**。当原问题为凸问题，KKT 条件是 $x^*,\lambda^*,v^*$ 为最优解的 ***充要条件*** 。


> 当原问题不是凸问题，则先通过 Slater 条件验证强对偶成立，再利用 KKT 求解，而当原问题是凸问题时，则可以直接利用 KKT 求解。

## Fritz Johns Condition

**The Fritz John Necessary Conditions**

$S\triangleq\{x\in X:g_i(x)\leq0\mathrm{~for~}i=1,...,m_1;h_j(x)=0\mathrm{~for~}j=1,...,m_2\}$ is the feasible region of Primal. Let $\bar{x} \in S$ be a local minimum of Primal. Then there exist $u \in \mathbb{R},v_1,\cdots, v_{m_1} \in \mathbb{R}$ and $w_1,\cdots,w_{m_2} \in \mathbb{R}$ such that

$$
\begin{aligned}
    u\nabla f(\bar{x})+\sum_{i=1}^{m_1}v_i\nabla g_i(\bar{x})+\sum_{j=1}^{m_2}w_j\nabla h_j(\bar{x})&=0, \\
    u,v_1 & \geq 0, \text{ for } i= 1,\cdots m_1\\
    (u,v_1,...,v_{m_1},w_1,...,w_{m_2})&\neq0
\end{aligned}
$$

Furthermore, in every neighborhood $\mathcal{N}$ of $\bar{x}$, there exists an $x' \in \mathcal{N}$ such that $v_i g_i (x') >0 $ for all $i \in \{ 1,\cdots ,m_1 \}$ with $v_i \neq 0$, and $w_j h_j > 0$ for all $j \in \{ 1,\cdots,m_2 \}$ with $w_j \neq 0$.

> 这个 furthermore 代表什么意义

**Fritz John’s theorem can be used to derive the Karush-Kuhn-Tucker theorem**

Let $\bar{x} \in S$ be a local minimum of Primal. Let $I = \{ i \in \{ 1,\cdots,m \} : g_i(\bar{x}) =0 \}$  be the index set for the active constraints. Suppose that $\bar{x}$ is regular; i.e. the family $\{\nabla g_i(\bar{x})\}_{i\in I}\cup\{\nabla h_j(\bar{x})\}_{j=1}^{m_2}$ of vectors is linearly independent. Then, there exist $v_1,...,v_{m_1}\in\mathbb{R}$ and $w_1,...,w_{m_2}\in\mathbb{R}$ such that

$$
\begin{aligned}
    \nabla f(\bar{x})+\sum_{i=1}^{m_1}v_i\nabla g_i(\bar{x})+\sum_{j=1}^{m_2}w_j\nabla h_j(\bar{x})&=0, \\
    & v_i \geq 0 \text{ for } i=1,\cdots,m_1
\end{aligned}
$$

Furthermore, in every neighborhood $\mathcal{N}$ of $\bar{x}$, there exists an $x' \in \mathcal{N}$ such that $v_i g_i (x') >0 $ for all $i \in \{ 1,\cdots ,m_1 \}$ with $v_i \neq 0$, and $w_j h_j > 0$ for all $j \in \{ 1,\cdots,m_2 \}$ with $w_j \neq 0$.





