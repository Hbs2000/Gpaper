# Portfolio Selection with Parameter and Model Uncertainty: A Multi-Prior Approach

Garlappi<sup>1</sup>, Lorenzo<sup>2</sup>, Raman Uppal<sup>3</sup>, and Tan Wang. ***The Review of Financial Studies***, 2007


1. *University of Texas at Austin*
2. *London Business School and CEPR*
3. *University of British Columbia and CCFR*


## Portfolio Choice

在本节中，Ambiguity 与 Uncertainty 等价。

### Model without Ambiguity Aversion

#### The classical mean-variance portfolio choice <!-- {docsify-ignore} -->

经典的马科维茨模型包含 $N$ 个风险资产，通过以下最优化问题求解 $w$：

$$\begin{equation}
\underset{w}{max} \ w^T \mu - {\gamma\over2}w^T\Sigma w
\end{equation}$$

其中 $\mu$ 是 N 维预期超额收益率向量，$\Sigma$ 是 $N\times N$ 维协方差矩阵，标量 $\gamma$ 是风险厌恶系数。该最优化问题的解为：
$$
\begin{equation}
w = {1\over \gamma} \Sigma^{-1} \mu
\end{equation}
$$

在实际情况中，我们并不知道 $\mu$ 的取值，因此需要用 $\hat{\mu}$ 来代替。因此，最优化问题转化为：

$$
\begin{equation}
    \underset{w}{max} \ w^T \hat{\mu} - {\gamma\over2}w^T\Sigma w
\end{equation}
$$

只有当期望收益率可以被精准估计时，即 $\hat{\mu} = \mu$，二者才等价，但是往往期望收益率极难估计，因此式（1）得到的解通常极不稳定，样本外表现很差。

> [!TIP|label: Starting point]
> 之所以选择 Markowitz (1952) 的静态均值方差优化作为出发点，而非 Merton (1971) 的动态模型，是由于以下几个原因：
>
> （1）本文要进行模型厌恶模型与模糊中性的贝叶斯模型比较，而贝叶斯模型往往是静态的【Jorion (1985, 1986, 1991, 1992), Pastor (2000), Pastor and Stambaugh (2000)】
>
> （2）静态模型可以帮助我们得到清晰的表达式，因此能够增进我们对于模糊模型概念的了解
>
> （3）在许多情况下，静态模型与动态模型最终得到的投资组合非常类似，这是因为二者的差别主要在于 *intertemporal hedging component*，而当模型根据return-generating parameters校准后，这一项往往很小。【动态模型文献：单个资产，Maenhout (2004)；多个资产 Chen and Epstein (2002), Epstein and Miao (2003), Uppal and Wang (2003)】


### Ambituity Aversion Model

为了衡量期望收益率估计带来的误差，我们需要在标准均值优化中引入两个新的Component：

1. 施加一个**额外限制**，使得每个资产的期望收益率都在其 *估计值的置信区间* 内
2. 加入一个**额外优化**，令每个投资者最小化在额外限制当中的期望收益率与模型选择

额外限制意味着投资者清楚地意识到估计误差存在的可能性，而额外优化反映了投资者对模糊的厌恶程度 (Gilboa and Schmeidler, 1989)。

因而，最优化问题变为：

$$
\begin{align}
&\underset{w}{max} \ \underset{\mu}{min} \ w^T\mu - {\gamma\over2}w^T\Sigma w \\
&\text{s.t.} \quad f(\mu,\hat{\mu},\Sigma) \leq \epsilon \quad w^T\bm{1} = 1
\end{align}
$$

权重加和为1的限制是因为不存在无风险资产，当存在无风险资产时，该限制可以去除。

需要注意的是，参数 $\epsilon$ 代表了模糊厌恶 (ambituity aversion, **common across assets**) 和厌恶 (ambiguity, **asset-specific**) 的乘积<sup>**T**</sup>。

> [!TIP|label:T]
> 这种区别就类似于风险厌恶与风险，前者是普遍的偏好，而后者 specific for each assets

而因为模糊程度与模糊二者在模型中并不能很好的区分开 (not observationally separable)，为了简化模糊偏好的表达，可以**将模糊厌恶程度标准化为1**。在本文的模型中，*投资者并不会选择模糊厌恶的程度，而只会关心每个资产不同的模糊程度* (asset-specific level of ambiguity)。

下文可以看到，在这种表达下，当假设先验为高斯分布后，参数 $\epsilon$ **在统计上**就可以被理解为**置信区间的大小**。










