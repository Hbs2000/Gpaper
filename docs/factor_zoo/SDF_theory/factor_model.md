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



## 6.2 General Factor Models 

在绝大多数情况下，我们使用的因子模型中的因子都是收益率，例如 CAPM 或 Fama-French 模型，有时候也会使用宏观变量作为因子，例如 GDP 的变化幅度。事实上，使用宏观变量而非收益率作为因子更加符合直觉，但接下来我们会看到，用收益率作为因子并不失一般性，因为我们可以**把其他因子投影到由收益率张成的空间中**，并把这些投影当作因子，这也就意味着，其他因子也可由收益率表征。。

使用收益率作为因子有一个好处就是可以很方便地确定风险价格，对于收益率来说，其风险价格就是**收益率的均值**，但是对于宏观变量等 general factor，其风险价格 **is not determined by theory**。

因子模型与 SDF 渊源颇深。对于任一因子模型，并且 $R_z \neq 0$，该模型因子的 affine function 就是 SDF，反之同理，如果 SDF 是一些随机变量的 affine function，并且均值不为 0，那么就存在一个以这些随机变量为因子的因子模型。因此，**找因子模型也就等价于在找 SDF 和 affine function**。

因子模型与 mean-variance analysis 也有着密不可分的关系。

> There is a factor model with a single return as the factor **if and only if** the return is on the mean-variance frontier (and not equal to the risk-free return if there is a risk-free asset or to the GMV return if there is no risk-free asset)


<div class = 'centerwords'>

Factor Models Are Equivalent to SDFs
</div>








