# Implications of security market data for models of dynamic economies
Hansen, Lars Peter<sup>1</sup>, and Ravi Jagannathan<sup>2</sup>, ***Journal of Political Economy***, 1991.

1. *University of Chicago, National Bureau of Economic Research*
2. *University of Minnesota and Federal Reserve Bank of Minneapolis*

In a rich class of models of dynamic economies，这些模型可能因为消费者偏好的异质性、由 tradable security 张成的 payoff 空间、或是 the role of money in the acquisition of consumption goods 不同而不同，但是**这些模型有一个共同的 implication**，any traded security can be represented as the expectation (conditioned on current information) of the product of the payoff and a SDF of any consumer。因此，**价格信息实际上隐含了关于 SDF 的性质**。

如果是从完备市场中得到的资产价格数据，那么通过 Arrow-Debreu 证券就可以得到 SDF。然而，首先，目前的金融市场很可能是不完备的，其次，经济学家也往往倾向于使用一部分的数据而非全部市场的数据进行分析。由于这些限制，*asset market data alone are typically not sufficient to identify IMRSs*.

在之前最常见的识别 SDF 方法是基于经济学家的观察，通过特定的方程表达出有关 SDF 的关系【habit model，recursive utility】。这些方法对各类资产定价模型施加了很强的假设【例如消费模型，效用函数】，通过选取特定的参数【如风险厌恶系数】来测试模型是否符合数据。

而本文对于各类资产定价模型施加尽可能少的限制，只保留了一价定律【law of one price: portfolios with the same payoffs have the same price】以及无套利原理【the absence of arbitrage opportunities: non-negative payoffs that are positive with positive probability have positive price】。

尽管我们不能完全观测到 SDF，但是仍然可以从数据中得到有关 SDF 的信息。

当 SDF 为常数，对于任意两个资产，如果他们的价格相同，那么其 payoff 的均值也一定相同。

$$
\text{If m is constant} \quad p = E[mx] = m E[x]
$$

而当两个资产价格相同，而 payoff 均值不同，则说明 SDF 一定不为常数。通过这一点，就可以得到 SDF volatility的lower bound。

本文提出的lower bound，可以作为资产定价模型【*无论是否为parametric*】的 diagnostic，并且这种方法可以让我们看出 which asset market data 对 SDF 提出了最严格的限制以及对资产定价模型提出最有意义的implications。

> [!NOTE|label:Volatility bound]
> SDF 的 Volatility bound 最早由 Shiller (1982) 提出，其目标是想为一类对数据不敏感的资产定价模型提出一个 diagnostic【即通过calibration不能验证模型的正确性】。但是在 Shiller (1982) 的例子中只包括两类资产，而本文并没有这一限制，并且即使在两类资产的情况下， Shiller (1982) 所得到的 volatility implication 也弱于本文。
>
> Grossman S J, Shiller R J. Consumption correlatedness and risk measurement in economies with non-traded assets and heterogeneous information[J]. ***Journal of Financial Economics***, 1982, 10(2): 195-210.

尽管同为得到 Volatility bound，但本文的出发点与 Shiller (1982) 不同.

1. 目前文献中关于SDF的研究，常用的是（如上文所说）给定某一函数形式的参数化方法，而本文提出的**非参数化方法**给这一领域提供了有益补充。例如，为什么某些模型会被统计检验拒绝？是因为参数化方法限制了 SDF 的variability吗？

2. 本文的所提出的diagnostic适用范围非常广泛，无论是通过观察数据得出 SDF 性质的参数化方法还是通过随机分析方法得出的结论。

3. 通过本文的方法，还可以得到是哪一类资产数据对 SDF 提出了最 stringent 的限制，进而对 dynamic economic model 提出了最 startling 的结论。此方法使得我们在进行此类对比时不必拘泥于特定的模型。

整体看来，本文的方法最大的特点就是通用（**common**）。

通过下图，可以更加清晰地阐述这些点：

<div align='center'>

![](../image/20230524PP1.png)
</div>

该图通过 1891-1985 股票和债券的年数据得到了一个 restricted region for the mean and standard deviations of SDF。 阴影部分区域给出了关于 SDF 均值和标准差的admissible pairs。【admissible: **allowed to be used**】

作为对比，这里还列出了 representative consumer model with commonly used period utility functions 所得到的 SDF 形式，其数值在图中用方块表示：

$$
U(c) = {c^{\gamma+1}-1 \over \gamma + 1} \quad \gamma \text{ is negative}
$$

小方块标准差不断升高的过程也代表了 $\gamma$ 在不断提高，并且标准差和均值之间的关系并不是一成不变的，可以看到随着标准差不断提高，其 SDF 的均值先下降后提高。

在 Section III 中，不考虑 SDF 需要为正数，因此，最小方差随机变量是资产payoff的线性组合。并且，SDF 的均值标准差前沿与资产 payoff 的均值方差前沿之间具有**对偶性**。这也实际上在说，通过 payoff 的前沿就足以构造出 SDF 前沿。因此，通过因子模型构造出 payoff 前沿也就意味着可以通过因子模型构造出 SDF 前沿。

在 Section IV 中，设定 SDF 为正数。此时最小方差组合不再需要是资产 payoff 的线性组合，而是这些payoff的欧式看跌看涨期权【**非线性**】。与 Section III 不同的是，此时对于某些预先给定的 SDF 均值，可能并不存在 nonnegative random variables with finite second moments that **behave like SDF**。尽管这一限制会使得 volatility bound more restrictive (thus more informative)，these sharper bounds are harder to compute。


对于任意预先给定的 SDF 均值，都能找到一个最小方差，因此构造了 SDF 的均值方差前沿。并且作者还发现了该均值方差前沿与我们熟悉的资产回报的均值方差前沿之间的**对偶性**。



## A General Model of Asset Pricing

<div style = 'display: none'>
$ \pi_I(p) $ 是在未来第 $\tau$ 期payoff为 p 的资产在第 0 期的价格， $mu_0^j,mu_{\tau}^j $ 分别是在零期和 $\tau$ 期的边际消费效用，$I^j$ 为第0期的information set，因此均衡为：

$$
\begin{equation}
mu_0^j \pi_I(p) =  E[mu_{\tau}^j p |I^j] \quad \text{for all p in P}
\end{equation}
$$

按照经济学理论，尽管边际效用不断递减，但应该始终为正【consumer is not satiated】，两侧同时除 $mu_0^j$，令 $m_j = mu_{\tau}^j / mu_0^j $，可以得到：
    
$$
\begin{equation}
mu_0^j \pi_I(p) =  E[m^j p |I^j] \quad \text{for all p in P}
\end{equation}
$$

当世界上信息完全公开，并且为完备市场时，所有消费者的 SDF 均相等。在这样的条件下，当 P 足够多，则可以确定**唯一的 SDF**。
</div>

接下来从这一公式入手，分析 m 的关系。

$$\begin{equation}
\bm{q} = E(\bm{x}m/I)
\end{equation}
$$

如果想要从实证角度研究这一公式中 m 的关系，必须要想办法得到关于 payoff，price，以及 information set 的数据。如同 Hansen and Richard (1987) 中的做法，本文 imagine an environment，在这个环境中始终满足该公式。通常来说我们认为经济学家能够获得关于 $\bm{x}_t, \bm{q}_t $ 的数据，并且 $\{ m_t,\ \bm{x}_t,\ \bm{q}_t\} $ 满足大数定律，即当样本规模极大时，样本矩趋于总体矩。

尽管资产价格在资产 payoff 实现的 $\tau$ 期之前就已经确定了，但是我们还是将价格序列 $\bm{q}_t$ 建模为 stochastic process，用以捕捉资产价格中可能出现的扰动。

此外，我们使用**无条件期望**来代表样本矩时间序列均值的 limit point。

> [!NOTE|label: Unconditonal expectations]
> When the time series converges appropriately to a stochastic steady state and is ergodic, unconditional expectations are computed using the stationary distribution.
>
> For processes that are asymptotically stationary but not ergodic, the limit points can be represented as conditional expectations in which the conditioning occurs on the invariant sets for the approxiamting stationary stochastic process.

对于该模拟环境中的序列 $\{ m_t,\ \bm{x}_t,\ \bm{q}_t\} $，我们做出以下假设：

#### Assumption 1 <!-- {docsify-ignore} -->

$ E|m|^2 < \infty,\ E|\bm{x}|^2 < \infty,\ E\bm{x}\bm{x}' \text{ is nonsingular, and } E|\bm{q}|<\infty$

Nonsingular的假设用以防止 $\bm{x}$ 是线性相关的情况，并且这也保证了**一价定律**成立。而对于 $\bm{x},\ \bm{q}$ 来说，即使原本的资产向量不满足这两个 moment restriction，但是也可以通过放缩使得其成立【因为价格和payoff在等式左右两侧】。 

而在该假设基础上应用 the law of iterated expectiations，消除条件信息，就得到了以下restriction：

**Restriction 1.** $E\bm{q} = E\bm{x}m $

Restriction 1将原本的定价模型从 conditional 转变为了 unconditional，因为通常来说 unconditional 比 conditional 更好估计。但是 in general，unconditional 的限制条件弱于 conditional。

**Restriction 2.** $ m > 0 $

Restriction 2 是无套利的充分条件。



### Implications of Restriction 1

<div class = 'centerwords'>

Riskless Payoff
</div>

存在无风险资产和不存在无风险资产是两种情况，前者比较容易分析，先从此处入手。

无风险资产在未来的 payoff 为1，且概率为1。首先构建一个未来 payoff 空间中的随机变量 $m* = \bm{x}\bm{\alpha}_0$，因此 Restriction 1可以写作：

$$\begin{equation}
E \bm{x}\bm{x}'\bm{\alpha}_0 = E\bm{q}
\end{equation}$$

解得 $\bm{\alpha}_0 = (E \bm{x}\bm{x})'E\bm{q}$。此时 $\bm{\alpha}_0$ 只依赖于 payoff 的二阶矩和 pirce 的一阶矩，也就意味着可以通过 asset market data 计算得出。

对于任意另一个满足 Restriction 1的随机变量 m，因为此时存在无风险资产，因此未来 payoff x 为1，此时所有 m 均值相同：
$$
Em = Em*
$$

因此有：
$$
E[\bm{x}(m-m*)] = 0
$$

这也意味着 $m$ 与 $m*$ 二者之差与随机向量 $\bm{x}$ 正交，因为 $m*$ 在 payoff 空间 P 中，因此可以理解为：$m*$ 是 $m$ 向 P 的**最小二乘投影**。

为什么要找方差最小的 $m*$，是因为只有 $m*$ 是 m 的投影时，其方差才最小。并且其他的 $m*$ 都不属于 payoff space 空间内，因此无法给出具体表达式。


根据equation 12，越偏离风险中性定价，则 $m*$ 的方差越大，bound越高


factor analysis就是一价定律

<div class = 'centerwords'>

No Riskless Payoff
</div>


### Implications of Restriction 2




