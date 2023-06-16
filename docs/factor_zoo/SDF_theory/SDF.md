# Stochastic Discount Factors

**Source**: *Asset Pricing and Portfolio choice theory*, Kerry E. Back, 2017, Chapter 3

**Contents**

3.1 Basic Relationships Regarding SDFs 

3.2 Arbitrage, the Law of One Price, and Existence of SDFs 

3.3 Complete Markets and Uniqueness of the SDF 

3.4 Risk-Neutral Probabilities 

3.5 Orthogonal Projections of SDFs onto the Asset Span

3.6 Hansen-Jagannathan Bounds 

3.7 Hedging and Optimal Portfolios with Quadratic Utility

3.8 Hilbert Spaces and Gram-Schmidt Orthogonalization 

3.9 Notes and References


## 3.2 Arbitrage, the Law of One Price, and Existence of SDFs 

无套利，一价定律，与 SDF 三者关系如下：

<div align = 'center'>

![](../image/20230616PP1.jpg)
</div>

如果不存在套利机会，那么一价定律一定成立：反过来说，如果一价定律不成立，那么一定存在套利机会。因此，无套利的假设强于一价定律。

一价定律和无套利原理能够使得我们在不假设任何有关效用函数，aggregation，完备市场的情况下得到有关 SDF 的性质。

本节的所有讨论在未来状态有限和无限时均成立。为了便利起见，此处仅给出有限状态下的证明。

<div class = 'centerwords'>

LOOP is equivalent to the existence of an SDF 
</div>

当存在 SDF 时，易得一价定律成立：

$$
\text{If payoff } x = y+z, \text{ then price } E(mx) = E[m(y+z)]
$$

接下来证明当一价定律成立，则 SDF 存在：

当一价定律成立，此时存在唯一 state-price vector q，满足以下公式：

$$
\begin{pmatrix}
x_{11}&\cdots&x_{1k}\\ \vdots&\vdots&\vdots\\ x_{n1}&\cdots&x_{nk}\end{pmatrix}
\begin{pmatrix}q_1\\ \vdots\\ q_k\end{pmatrix} = 
\begin{pmatrix}p_1\\ \vdots\\ p_n
\end{pmatrix}
$$

x 是资产 payoff，q 是 Arrow security 的价格，而 p 是资产价格。此时并没有假定 n 与 k 之间的数量关系，k 可以大于、等于或小于n。

以矩阵表示为：

$$
\begin{equation}
X q = p
\end{equation}
$$

在 Arrow security 中，存在定价公式【不基于一价定律】：

$$
\tilde{m}(\omega_j)=q_j/\text{prob}_j.
$$

因此，逻辑是：**只有一价定律成立，才能得到唯一的 q，进而基于 Arrow security 得到 SDF 的公式**。

$$
\begin{aligned}
p_{i}=\sum_{j=1}^k x_{i j}q_{j}=\sum_{j=1}^k x_{i j}m_{j}\mathrm{prob}_{j}\stackrel{\mathrm{def}}{=}\mathsf{E}[\tilde{x}_{i}\tilde{m}]. 
\end{aligned}
$$


#### Cochrane's view <!-- {docsify-ignore} -->

**唯一的state price vector q，实际上就是 $x^*$。**

<div align = 'center'>

![](../image/20230616PP2.png)
</div>


对于 payoff 一样的资产，当前 price 应该一样，反之亦然，**当 price 一样，那么未来 payoff 应该也一样**，否则同样意味着套利机会。

也就是说，price=1 这条直线代表了一个随机变量，这一直线上的不同点代表着这一随机变量在不同 state 下分别的 payoff 略有区别，但整体【联合各状态下 payoff】来看还是等价的。因此，满足一价定律时，也就意味着存在 $x^*$，此时 $x^*$ 也就是 SDF。

因为 $x^*$ 存在于 payoff 空间中，其也可以由 x 线性表示，$x^* = c'x$，因此有：

$$
\begin{aligned}
& p = E(x*x) = E(xx'c) \\
& \Rightarrow c = E(x'x)^{-1}p \\
& \Rightarrow x^* = p'E(xx')^{-1}x
\end{aligned}
$$


<div class = 'centerwords'>

No arbitrage means a strictly positive SDF
</div>

一价定律能够推出 SDF 存在，但并不能得到严格为正的 SDF。

无套利能够推出严格为正的 SDF，**反之同样成立**，严格为正的 SDF 也意味着无套利。

如果此时不存在套利机会，则意味着零向量是 M 中唯一的非负向量。根据 *Tucker's Complementarity Theorem*，此时存在一个严格为正且与 M 正交的向量 $\bm{v}$，满足 $v'Y\theta = 0 \text{ for all } \theta \in \mathcal{R}^n $。

因此，展开有：
$$
-v_1p'\theta+(v_2\cdots v_{k+1})X'\theta=0
$$

which implies that：

$$\begin{aligned}
q'X'\theta &= p' \theta \\
p &= Xq
\end{aligned}$$

因此，得到了严格为正的 state price vector q。

#### Cochrane's view <!-- {docsify-ignore} -->

此处讨论的套利与一般意义上人们常说的套利是不同的。通常来说，套利表示对一价定律的违反，而在本节，无套利代表 you can’t get for free a portfolio that might pay off positively, but will certainly never cost you anything.

当 $m>0$，易得无套利。当 $m>0$，而 payoff 非负并且在某些 state 下大于0，则代表在某些状态下 $mx>0$，在另外一些状态下 $mx=0$，因此 $E(mx)=p>0$。

接下来从无套利推出 $m>0$。

在完备市场中，通过反证法可得出。无套利可推出一价定律，因此有 $p=E(x^*x)$，此时只存在一个 SDF。假设在某些 states 下 $x^*<0$，此时存在 Arrow security 在该 state 下 payoff为1，其余状态下为0，那么 $ \sum \pi(s)x^*(s)$ 为负，违反无套利，因此 $m>0$。

当市场不完备时，存在许多 SDF，$m = x* + \varepsilon \text{ with } E(\varepsilon x)=0$。此时我们需要说明**至少一个 SDF 为正**，但这个 SDF 可能不是 $x*$，即可能不在 payoff 空间中。此时有另外的证明方法，在此不具体列出。

无套利原理说明了存在一个严格为正的 SDF，但并没有说 SDF **唯一**，只有当市场为完备市场时，SDF 才是唯一的。


## 3.5 Orthogonal Projections of SDFs onto the Asset Span

对于任何finite-variance SDF $\tilde{m}$，都等同于 $\tilde{m}_p+\tilde{\epsilon}$，其中 $\tilde{m}_p$ 是由资产张成的**唯一的** SDF，而 $\tilde{\epsilon}$ 与这些资产正交。

由资产张成的含义是：$\tilde{m}_p$ 是资产payoff的线性组合，而正交的意思是 $E[\tilde{\epsilon} \tilde{x}_i] = 0$，而 **$\tilde{m}_p$ 被称之为 $\tilde{m}$ 在资产所张成空间上的正交投影**。

因为 $\tilde{m}_p$ 也可以被当作payoff，那么根据定价公式，其价格为：

$$
P = E[mx] = E[\tilde{m}_p^2]
$$

用 payoff 除价格得到收益率：

$$
\tilde{R}_p =  {\tilde{m}_p \over E[\tilde{m}_p^2] }
$$


<div class = 'centerwords'>

Projections and Regressions
</div>

**通过线性回归的解释来理解SDF**

在有限维情况下，正交投影与线性回归本质上是一回事，正常的线性回归方程如下：

$$
y = X\hat{\beta}+\varepsilon
$$

将 $X\hat{\beta}$ 记为 $y_p， \text{p for predicted or projected}$。$y_p$ 的形式实际上是 $X$ 矩阵中column的线性组合，也即X中的column张成了这一空间。

选取向量 $\hat{\beta}$ 最小化平方误差和 $(y-y_p)'(y-y_p)$，也就是在 columns of X 张成的空间中找距离 $y$ 最近的 $y_p$，那么也就是找 $y_p$ 使得**误差 $\varepsilon = y-y_p$ 与 columns of X 正交**，也即：

$$
X'(y-X\hat{\beta}) = 0
$$

当 $X'X$ 可逆，有

$$
\begin{equation}
\hat{\beta} = (X'X)^{-1}X'y \quad \text{and} \quad y_p = X(X'X)^{-1}X'y
\end{equation}
$$

<div align ='center'>

![](../image/20230511PP1.png)
</div>

**$\tilde{m}_p$ 的角色与 $y_p$ 是很类似的。**

当资产 payoff $x_i$ 的方差是有限的，并且满足一价定律时，此时存在 SDF $\tilde{m}$ with finite variance。将其投影到 the span of the assets，而当所有资产价格均为正数时，同样可以将其投影到 the span of returns，因为此时the span of the assets 等价于 the span of the returns。

$\tilde{X}$ 是资产payoff matrix，用 $\tilde{x}_i$ 代表其中的element，如果存在无风险资产，那么其回报也属于 $\tilde{X}$ 中的一列。$\tilde{m}_p$ 是资产payoff的线性组合意味着 $\tilde{m}_p = \tilde{X}'\theta$ 。

沿着完全同样的思路，有：

$$
E[\tilde{X}(\tilde{m}-\tilde{m}_p)] = E[\tilde{X}(\tilde{m}-\tilde{X}'\theta)] = 0
$$

> [!NOTE]
> $\tilde{X}(\tilde{m}-\tilde{X}'\theta)$ denotes multiplication of the **column vector** $\tilde{X}$ by the **scalar** $(\tilde{m}-\tilde{X}'\theta)$

求解过程如下：


$$
\begin{aligned}
E[\tilde{X}\tilde{m}] = E[\tilde{X}\tilde{X}']\theta & \Rightarrow \  \theta = E[\tilde{X}\tilde{X}']^{-1} E[\tilde{X}\tilde{m}] \\
& \Rightarrow \tilde{m}_p = E[\tilde{X}\tilde{m}]' E[\tilde{X}\tilde{X}']^{-1} \tilde{X}
\end{aligned}
$$

这里我们假定矩阵 $E[\tilde{X}\tilde{X}']$ 是可逆的。当其不可逆时，会有许多 $\theta$ 满足 $\tilde{m}_p = \tilde{X}'\theta$，**but the projection $\tilde{m}_p$ is still uniquely defined**。

因为有 $E[\tilde{X}\tilde{m}] = p$，因此上式可简化为：

$$
\tilde{m}_p = p' E[\tilde{X}\tilde{X}']^{-1} \tilde{X}
$$

**$\tilde{m}_p$ 的表达式中没有出现 $\tilde{m}$ 项，这意味着对于任何 $\tilde{m}$，最终投影都是唯一的。**

<div align = 'center'>

![](../image/20230511PP2.png)
</div>

实际上，上述公式**很少用到**，只需要知道其代表的性质就够了：**存在一个唯一的SDF，并且该SDF代表一个组合的payoff**。


<div class = 'centerwords'>

Projections That Include a Constant

</div>

本节介绍的 general formula for projections 更为常用，在下节就会应用到SDF上。

定义 $\tilde{Y}$ 为随机变量的 n 维向量，$\tilde{X}$ 是随机变量的 k 维向量，假定所有随机变量的方差均有限，则有：

$$
\operatorname{Cov}(\tilde{Y},\tilde{X})=\operatorname{E}[(\tilde{Y}-\overline{Y})(\tilde{X}-\overline{X}) ']
$$

其中 $\bar{Y} = E[\tilde{Y}],\ \bar{X} = E[\tilde{X}]$，$\operatorname{Cov}(\tilde{Y},\tilde{X})$ 为 $n\times k$ 维矩阵，

同样，将投影定义为回归，可以从如下公式出发：

$$\begin{equation}
\tilde{Y}=A+B\tilde{X}+\tilde{\varepsilon}
\end{equation}$$

其中，$ E[\tilde{\varepsilon}] = 0 $，定义：

$$
\begin{align}
B&=\text{Cov}(\tilde{Y},\tilde{X})\text{Cov}(\tilde{X})^{-1} \\
A&=\overline{Y}-B\overline{X} \\
\tilde{\varepsilon} &=\tilde{Y}-\overline{Y}-B(\tilde{X}-\overline{X}).
\end{align}
$$

其中 $A$ 是n维常数向量， $B$ 是 $n\times k$ 维矩阵。为了说明 $A+B\tilde{X}$ 是 $\tilde{Y}$ 的投影，需要证明 $E[\tilde{\varepsilon} \tilde{X}'] = 0 $，根据 $E[\tilde{\varepsilon}] = 0$，可知 $E[\tilde{\varepsilon}\bar{X}'] = 0$，因此有：

$$
E[\tilde{\varepsilon}\tilde{X}'] = E[\tilde{\varepsilon}(\tilde{X}-\bar{X})']
$$

代入得：

$$
\begin{aligned}
\textsf{E}[\tilde{\varepsilon}(\tilde{X}-\overline{X})']& =\mathsf E[(\tilde{Y}-\overline{Y})(\tilde{X}-\overline{X})']-B\mathsf E[(\tilde{X}-\overline{X})(\tilde{X}-\overline{X})']  \\
&=\mathrm{Cov}(\tilde{Y},\tilde{X})-B\mathrm{Cov}(\tilde{X}) \\
&=\operatorname{Cov}(\tilde{Y},\tilde{X})-\operatorname{Cov}(\tilde{Y},\tilde{X})=0.
\end{aligned}
$$

因此，$\tilde{Y}$ 的投影为：

$$
\begin{align}
A+B\tilde{X} = \overline{Y}+\operatorname{Cov}(\tilde{Y},\tilde{X})\operatorname{Cov}(\tilde{X})^{-1}(\tilde{X}-\overline{X})
\end{align}
$$

$\tilde{Y} \ \text{and } B, \tilde{X}$ 都是列向量，并且有着一一对应的关系，$\tilde{y}_i$ 是 $\tilde{X}$ 的线性组合，并且每一个线性组合都与对应的 $\tilde{y}_i$ 有最大的相关系数，证明如下：


$$
\operatorname{cov}(\tilde{y}_i,b'\tilde{X})=\operatorname{cov}(b_i\tilde{X},b'\tilde{X})+\operatorname{cov}(\tilde{\varepsilon}_i,b'\tilde{X})=\operatorname{cov}(b_i\tilde{X},b'\tilde{X})
$$

$$
\begin{aligned}
\text{corr}(\tilde y_i,b'\tilde X)& =\frac{\text{cov}(\tilde{y}_i,b'\tilde{X})}{\text{stdev}(\tilde{y}_i)\text{stdev}(b'\tilde{X})}  \\
&=\frac{\text{cov}(b'_i\tilde{X},b'\tilde{X})}{\text{stdev}(\tilde{y}_i)\text{stdev}(b'\tilde{X})} \\
&=\frac{\operatorname{corr}(b_i\tilde{X},b'\tilde{X})\operatorname{stdev}(b_i'\tilde{X})}{\operatorname{stdev}(\tilde{y}_i)}.
\end{aligned}
$$

当 $b = b_i$ 时有最大值。




