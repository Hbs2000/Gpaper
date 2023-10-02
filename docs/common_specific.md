# Common and specific

**Literature one**: Goyal A, Pérignon C, Villa C. How common are common return factors across the NYSE and Nasdaq?[J]. ***Journal of Financial Economics***, 2008, 90(3): 252-271.

作者利用**PCA**类方法，对NASDAQ和NYSE的股票分别测算，发现两类股票有两个common因子，同时分别有一个specific因子。

理论基础：the existence of **common** pervasive factors and **group-specific** pervasive factors is not ruled out by APT. The theory of APT permits both **observable** and **unobservable** factors

APT的return generating function为：
$$\begin{equation}
R = BF^K + \varepsilon 
\end{equation}
$$

K为总的因子数量。

本文设定对于每一group的return generating function为：

$$\begin{equation}
R^g = B^g F^{K_g} + \varepsilon_g
\end{equation}
$$

其中：$R_g$ 是group g的 $N_g \times T$ 维超额收益矩阵，$B_g$ 是 $N_g \times K_g$ 维因子系数矩阵，$F_g$ 是 $K_g \times T$ 维因子收益率矩阵。

而对于common和specific的定义为：

$$\begin{aligned}
\text{group-specific factors are a subset of }F^K : F^K &= \cup^G_{g=1} F^{K_g} \\
\text{common factors are given by : } K_c &= \cap^G_{g=1} F^{K_g}
\end{aligned}
$$



**Literature two**: Ando T, Bai J. Asset pricing with a general multifactor structure[J]. ***Journal of Financial Econometrics***, 2015, 13(3): 556-604.

类似于上一篇文章对于美国两个股市分别测算，这篇文章同样对于中国的AB股市场做了测算。不同的是，这篇文章还考虑了observable和unobservable的因子。

$$\begin{equation}
y_{it}=x_{it}^{\prime}\beta_{i}+f_{c,t}^{\prime}\lambda_{c,i}+f_{g_{i},t}^{\prime}\lambda_{g_{i},i}+\varepsilon_{i,t},\quad i=1,\ldots,N,t=1,\ldots,T.  
\end{equation}
$$

其中 $x_{i,t}$ 是observable risk factor，维度可以非常高；$f_{c}$ 是 ***unobservable common*** pervasive factors that affect the returns of all securities in all groups；$f_{g}$ 是 ***unobservable group-specific*** pervasive factors that affect the returns of securities only in specific group，common factor 与group-specific factor正交。

该文章最大的问题是 ***假设分组关系 $g_i$（group membership）已知。***


**Literature three**: Su L, Shi Z, Phillips P C B. Identifying latent structures in panel data[J]. ***Econometrica***, 2016, 84(6): 2215-2264.

文章提出的C-lasso同时实现了对于factor的分组和beta的估计，克服了上一篇文章的问题（unknown group membership）。

C-lasso的惩罚项如下：

$$\begin{equation}
Q_{1NT,\lambda_1}^{(K_0)}(\boldsymbol{\beta},\boldsymbol{\alpha})=\frac{1}{NT}\sum_{i=1}^N\sum_{t=1}^T\psi(w_{it};\beta_i,\hat{\mu}_i(\beta_i))+\frac{\lambda_1}N\sum_{i=1}^N\prod_{k=1}^{K_0}\|\beta_i-\alpha_k\|,
\end{equation}
$$





