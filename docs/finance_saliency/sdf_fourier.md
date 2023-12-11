# SDF and Fourier

## Return in Frequency domain

关于 SDF，有以下线性假定：

$$
\begin{align}
M_t = 1 - b'(f_t - E[f_t])
\end{align}
$$

以及无条件定价公式【将因子预期收益率作为**待被 SDF 定价的预期收益率**】：

$$\begin{align}
E[M_tf_t] = 0
\end{align}$$

若要式（1）式（2）同时满足，则 $b$ 有：

$$\begin{align}
b = \Sigma^{-1} E[f_t]
\end{align}$$

> [!TIP|label:Derivation]
$$
\begin{aligned}
    0' &= E[(1-b'(f_t-E[f_t]))f_t'] \\
    &= E[f_t]' - E[b'(f_t - E[f_t])f_t'] \\
    &= E[f_t]' - b' \Sigma
\end{aligned}
$$
>
> 如果我们对 SDF 中的 $f_t - E[f_t]$ 做傅里叶变换，并得到逆变换后不同频率的时间序列，就可以计算不同频率与 test asset $f_t$ 的协方差，那么就可以通过这种方式重构 $b$。
>
> 因为不可能所有因子的所有频率都是有用的，此时需要一个优化算法，来进行频率筛选。


式（3）可被重新表述为：

$$
\begin{equation}
    \begin{aligned}
        b &= (\Sigma \Sigma)^{-1} \Sigma E[f_t] \\
       \Longrightarrow \ b &= (\Sigma' \Sigma)^{-1} \Sigma' E[f_t] \quad   \Sigma \text{ is symmetric}  
    \end{aligned}
\end{equation}
$$

因为此时将因子预期收益率作为待被 SDF 定价的预期收益率，所以相当于将这些因子收益率回归到其自身的协方差矩阵回归上，则 **SDF 的系数恰好等于这个特殊的截面回归的系数**，并且，SDF 的系数也是 MVE 投资组合的投资权重。

但是，由于我们不知道数据的总体矩，因此只能通过样本矩来进行上述回归。

假如样本长度为 $T$，因子取值为 $f_t$，则有：

$$
\begin{align}
\bar{\mu} &= \frac{1}{T} \sum_{t=1}^T f_t \\
\bar{\Sigma} &= \frac{1}{T} \sum_{t=1}^T (f_t - \bar{\mu})(f_t - \bar{\mu})'
\end{align}
$$

则

$$
\begin{equation}
    \hat{b} = \bar{\Sigma}^{-1} \bar{\mu} 
\end{equation}
$$

然而，除非因子维度相对于样本长度而言非常小，否则这一朴素估计量将产生非常不准确的 $b$ 的估计值。根据 Kozak et al. (2020)，其中不准确的主要来源是对于 $\mu$ 的估计，可通过对 $\mu$ 施加先验来提高估计。

因此，尽管通过前文，可以对 $f_t - E[f_t]$ 做傅里叶分解，来提高估计，但是此举是通过优化**协方差矩阵**的方式进行改进，而非提高对 test asset $\mu$ 的估计。这块还要想一想。

## Covariance in Frequency domain

根据 Neuhierl and Varneskov (2021)，对于式（2），进一步变换得：

$$\begin{equation}
\begin{aligned}
E[f_t] &= -\frac{Cov(M_t,f_t)}{E[M_t]} \\
&= -\frac{1}{E[M_t]}\times\underbrace{Var(M_t)\boldsymbol{\beta}_{f,M}}_{\text{beta risk}}\times \underbrace{\sum_{j=1}^q\frac{\mathbf{Cov}_{f,M}(\vartheta_j,\vartheta_{j+1})}{\mathbf{Cov}(M_t,f_t)}}_{\text{frequency risk}}
\end{aligned}
\end{equation}
$$

其中，$\mathbf{Cov}_{f,M}(\vartheta_j,\vartheta_{j+1})$ 代表对资产 $f$ 和 SDF $M_t$ 的协方差做傅里叶分解后，取其中 $j \sim (j+1)$ 的频率部分。

感觉也有点意思，论文再看看。明天先按照第一个方向做一做。


1. Neuhierl A, Varneskov R T. Frequency dependent risk[J]. Journal of Financial Economics, 2021, 140(2): 644-675.
2. Kozak S, Nagel S, Santosh S. Shrinking the cross-section[J]. Journal of Financial Economics, 2020, 135(2): 271-292.