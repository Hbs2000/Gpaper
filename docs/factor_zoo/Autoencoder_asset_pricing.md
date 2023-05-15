# Autoencoder asset pricing models
Shihao Gu<sup>1</sup>, Bryan Kelly <sup>2</sup>,Dacheng Xiu<sup>1</sup>, ***Journal of Econometrics***, 2021

1. *Booth School of Business, University of Chicago*
2. *Yale University, AQR Capital Management, and NBER*


部分资产文献认为，characteristic-based asset return prediction属于一种异象（anomaly），然而，Kelly, Pruitt, and Su (KPS, 2019) 提出了IPCA，证明了这些特征实际上**proxy for unobservable and time-varying exposures to risk factors**，一旦这种factor exposure被纳入考量，这些特征也就不再产生 $\alpha$。

KPS的定价框架如下：

$$
\begin{equation}
r_{i,t} = \beta(z_{i,t-1})' f_t + u_{i,t}
\end{equation}
$$

其中，$f_t$ 是latent factor，$K\times1$ 维的条件因子暴露 $\beta(z_{i,t-1})$ 是 $P\times1$ 维资产特征，P一定大于K，并且很有可能维度很高。但是在KPS中，由特征到 $\beta$ 的映射十分简单，属于线性映射：

$$\begin{equation}
\beta(z_{i,t-1})' = z_{i,t-1}'\Gamma
\end{equation}$$

因此本文在此基础上将其提升为非线性。

更广泛的来说，本文提出了一个运用非参数方法估计SDF的模型，并且施加了经济学意义上无套利的限制。




















