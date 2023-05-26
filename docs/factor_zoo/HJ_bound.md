# Implications of security market data for models of dynamic economies
Hansen, Lars Peter<sup>1</sup>, and Ravi Jagannathan<sup>2</sup>, ***Journal of Political Economy***, 1991.

1. *University of Chicago, National Bureau of Economic Research*
2. *University of Minnesota and Federal Reserve Bank of Minneapolis*


Typically, asset market data alone are not sufficient to identify IMRSs.

在之前最常见的识别 SDF 方法是基于经济学家的观察，通过特定的方程表达出有关 SDF 的关系【habit model，recursive utility】。这些方法对各类资产定价模型施加了很强的假设【例如消费模型，效用函数】，通过选取特定的参数【如风险厌恶系数】来测试模型是否符合数据。

而本文对于各类资产定价模型施加尽可能少的限制，只保留了一价定律【law of one price: portfolios with the same payoffs have the same price】以及无套利原理【the absence of arbitrage opportunities: non-negative payoffs that are positive with positive probability have positive price】。

尽管我们不能完全观测到 SDF，但是仍然可以从数据中得到有关 SDF 的信息。

当 SDF 为常数，对于任意两个资产，如果他们的价格相同，那么其 payoff 的均值也一定相同。

$$
\text{If m is constant} \quad p = E[mx] = m E[x]
$$

而当两个资产价格相同，而 payoff 均值不同，则说明 SDF 一定不为常数。

通过这一点，就可以得到 SDF volatility的lower bound。


本文提出的lower bound，可以作为资产定价模型【*无论是否为parametric*】的 diagnostic，并且这种方法可以让我们看出 which asset market data 对 SDF 提出了最严格的限制以及对资产定价模型提出最有意义的implications。


对于任意预先给定的 SDF 均值，都能找到一个最小方差，因此构造了 SDF 的均值方差前沿。并且作者还发现了该均值方差前沿与我们熟悉的资产回报的均值方差前沿之间的**对偶性**。

<div align='center'>

![](image/20230524PP1.png)
</div>


## A General Model of Asset Pricing

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




<div class = 'centerwords'>

Restriction 1. $E\bm{q} = E\bm{x}m $
</div>

Restriction 1将原本的定价模型从 conditional 转变为了 unconditional，因为通常来说 unconditional 比 conditional 更好估计。但是 in general，unconditional 的限制条件弱于 conditional。


<div class = 'centerwords'>

Restriction 2. $ m > 0 $
</div>

Restriction 2 是无套利的充分条件。



### Implications of Restriction 1

为什么要找方差最小的 $m*$，是因为只有 $m*$ 是 m 的投影时，其方差才最小。并且其他的 $m*$ 都不属于 payoff space 空间内，因此无法给出具体表达式。


根据equation 12，越偏离风险中性定价，则 $m*$ 的方差越大，bound越高


factor analysis就是一价定律








