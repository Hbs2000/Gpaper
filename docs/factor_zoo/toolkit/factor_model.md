# Factor Models

**Source**: *Asset Pricing and Portfolio choice theory*, Kenrry Back, 2017, Chapter 6

**Contents**

6.1 Capital Asset Pricing Model 

6.2 General Factor Models 

6.3 Jensen’s Alpha and Performance Evaluation 

6.4 Statistical Factors 

6.5 Arbitrage Pricing Theory 

6.6 Empirical Performance of Popular Models 

6.7 Notes and References


有时我们称呼一个因子模型为因子定价模型（factor pricing model）或风险溢价因子模型（factor model for risk premia）。这种叫法是为了与统计因子模型（statistical factor model）区分开。统计因子模型解释了资产收益率与一些因子的协方差，而因子定价模型解释了因子的风险溢价。

然而，充分分散的股票组合的风险主要与协方差有关，因此统计因子模型应该也能够解释组合风险，那么其应该也能够解释风险溢价。换言之，统计因子模型应该也属于因子定价模型。

这种 $\text{statistical factor model} \Longrightarrow \text{factor pricing model} $，也就是APT理论。

根据第三章的内容，基础定价公式为：

$$\begin{equation}
E[\tilde{R}] = {1\over E[\tilde{m}]} - {1\over E[\tilde{m}]} cov(\tilde{m},\tilde{R})
\end{equation}
$$

对于任意收益率 $\tilde{R}$ 和 SDF $\tilde{m}$，当 $E[\tilde{m}] \neq 0$，都有上述公式成立。

当收益率与SDF之间**协方差为零**时，收益率为 ${1\over E[\tilde{m}]}$，这也称之为 zero-beta return，记为 $R_z$，因此式（1）可写为：

$$\begin{equation}
E[\tilde{R}]-R_z = -R_z cov(\tilde{m},\tilde{R})
\end{equation}$$

**所有的因子模型都是式（2）的一个特例**。


## 6.1 Capital Asset Pricing Model 




























