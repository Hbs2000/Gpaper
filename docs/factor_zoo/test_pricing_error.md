# Testing Pricing Errors of Models with Latent Factors and Firm Characteristics as Covariances

Zhang Chu<sup>1</sup>. ***Management Science***, 2023

1. *Hong Kong University of Science and Technology, Hong Kong*



研究问题：$\alpha \text{ and } \beta $ 


## Orthogonality

$\alpha \text{ and } \beta $ should be orthogonal


### APT

[【Reference: 石川】](https://zhuanlan.zhihu.com/p/260114845)

**Step one**

$$
R_i=\mu_i+\beta_if+\varepsilon_i,\quad i=1,\cdots,n
$$

where $E[f] = E[\epsilon_i] = 0$, in vector form:

$$
R=\mu+f\boldsymbol{\beta}+\boldsymbol{\varepsilon}
$$

**Step two**

Construct an arbitrage portfolio:

- zero cost: $\boldsymbol{w}'\boldsymbol{e}=0$
- the arbitrage portfolio's return $R_a=\boldsymbol{\omega}'\boldsymbol{R}=\boldsymbol{\omega}'\boldsymbol{\mu}+\boldsymbol{\omega}'\boldsymbol{\beta}f+\boldsymbol{\omega}'\boldsymbol{\varepsilon}$
- the a-portfolio has no exposure to risk factor: $\boldsymbol{w}'\beta = 0$

**Step three**

The portfolio which has zero cost and zero risk deserve zero return:

$$
R_a=\omega^{\prime}\boldsymbol{\mu}=0
$$

Three perpendicular conditons means:

> Vector $w$ is perpendicular to $\mu,\beta,e$, which means $\mu$ must be in the space spanned by $\beta \text{ and } e$

$$
\boldsymbol{\mu}=\gamma_1\boldsymbol{e}+\gamma_2\boldsymbol{\beta}
$$

$\gamma_1$ is the *zero-beta return*, which is risk-free return if it exists. 

And if we assume there is only one factor and take market portfolio to the model, we will get CAPM *elegantly*.

$$\begin{aligned}
\mu_m=R_f+\gamma_2\times1 & \Longrightarrow  \gamma_{2}=\mu_{m}-R_{f} \\
\Longrightarrow \mu_i=R_f&+\beta_i(\mu_m-R_f)
\end{aligned}$$

在此基础上进行扩展，即可得到多因子模型：

$$\begin{equation}
\operatorname{E}[R_i^e]=\mu_i-R_f=\beta_{i1}\lambda_1+\beta_{i2}\lambda_2+\cdots+\beta_{iK}\lambda_K
\end{equation}
$$

#### More about APT <!-- {docsify-ignore} -->

*那么我们所说的 Orthogonality 应该体现在什么地方呢？*

In Finance, the only thing we care about is the **cross-sectional difference**, namely, why different assets earn different returns, which can be tested by cross-sectional regression:

$$
E_T[R_i^e] = \hat{\beta}'_i \boldsymbol{\lambda} + \varepsilon_i, \quad i = 1,2,\cdots,N
$$

**NO intercept**

在进行截面回归时，背后最基础的假设为: risk-based interpretation。

也就是说，当不存在 $\beta$ 时，资产的收益率应该等于无风险收益率或 zero-beta return，而将 $r_f$ 移至左侧，因变量为超额收益率时，此时在 risk-based interpretation 下，**不应存在截距项**，因此，<mark>**模型回归出的残差才应该作为 pricing error**</mark>。

Orthogonality 也恰恰体现于此，$\varepsilon$ 与 $\beta$ 正交，并且残差满足 $\boldsymbol{1}'\boldsymbol{\varepsilon} = 0$。

> 按理说intercept是coefficient中的一部分，二者不可能做到正交，所以只有是residual才能实现

> [!NOTE|label:In a nutshell]
> the orthogonality conditon $B'_t \alpha_t = 0_k$, which *is the heart of APT*, and is important in order to obtain an ***unambiguous interpretation*** of the term as a pricing error

> [!WARNING|label:Time series regression]
> 在时序回归中并非如此。

### IPCA

$$\begin{equation}
r_{t+1}=Z_{t}\Gamma_{\alpha}+Z_{t}\Gamma_{\beta}f_{t+1}+\varepsilon_{t+1},\quad t=1,\ldots,T.
\end{equation}
$$


**Restriction**

In IPCA, $B_t^{\prime}\alpha_t=\Gamma_\beta^{\prime}Z_t^{\prime}Z_t\Gamma_\alpha=0_k$, which is **impossible** for any constant $\Gamma_\alpha$ and $\Gamma_\beta$ when $Z_t$ is time-varying.

Instead, due to under-identified caused by the overwhelming number of parameters, IPCA imposes an orthogonality condition $\Gamma_{\beta}'\Gamma_{\alpha}=0$.

**From unconditional to conditional**

why is there $\alpha$ and $\epsilon$ at the same time?

为什么在做时序回归时，我们认为intercept是pricing error，但是在截面回归时我们认为residual是pricing error

> 截面回归是没有截距项的，epsilon就代表了定价误差，因为在多因子模型的假设中，截面收益率差异仅由common factor和specific beta决定。然而时序回归不是为了最小化alpha，而是为了拟合收益率序列，也即R square最大，因此收益率存在intercept。而当截面模型加入了时序的成分，也就是conditional model

为什么IPCA中截距项是pricing error，Autoencoder里residual是pricing error


<hr>


## Dissecting the orthogonality

**New specification**

$$\begin{equation}
r_{t+1}= \underbrace{P_{ot}\delta_o+P_{it}\delta_i}_{\boldsymbol{\alpha}} +\underbrace{(Z_t+1_n\psi')\Gamma}_{\boldsymbol{\beta}} f_{t+1}+\varepsilon_{t+1},\quad t=1,\ldots,T 
\end{equation}$$

- $r_{t+1}$ is an $n$-vector of asset returns in excess of the risk-free rate from $t$ to $t+1$
- $Z_t$ is $n\times l$ firm characteristics at $t$ with $n \geq l$, $1_n$ is an $n$-vector of ones 
- $\psi$ is an $l$-vector of constants
- $\Gamma$ is an $l \times k$ matrix of full column rank with $k \leq l$

> The condition $\Gamma$ has full column rank is to remove redundancy. 

- $\delta=(\delta_0^{\prime},\delta_i^{\prime})^{\prime}$ is an $(n-k)$-vector of constants in which the dimension of $\delta_0$ and $\delta_i$ are $n-l$ and $l-k$ respectively
- $f_{t+1}$ is a $k$-vector of latent systematic factors realized at $t+1$ with mean $\mu_f$ and variance $\Omega_f$
- $P_t = (P_{ot},P_{it}) $ is an $n \times (n-k) $ **orthonormal basis** that is orthogonal to $(Z_t+1_n\psi')\Gamma$, $P_{ot}$ is $n\times (n-l)$ if $n>l$, orthogonal to the subspace spanned by $Z_{t}^{*}=Z_{t}+1_{n}\psi^{\prime}$, $P_{it}$ is $n\times (l-k)$ if $l>k$ within the subspace spanned by $Z_{t}^{*}$ but orthogonal to the subspace spanned by $Z_{t}^{*} \Gamma$

$P_t \delta$ satisfying $B_{t}^{\prime}\alpha_{t}=[(Z_{t}+1_n{\psi^{\prime}})\Gamma]^{\prime}(P_t\delta)=0_k$

> **The inside-model pricing error** in the case of $l> k$ is within the $l$-dimensional subspace spanned by the affine-transformed firm characteristics but orthogonal to the $k$-dimensional subspace of the factor beta. 
> 
> **The outside-model pricing error** in the case of $n>l$ is orthogonal to the $l$-dimensional subspace spanned by the affine-transformed firm characteristics.

- $\epsilon_{t+1}$ is an $n$-vector of idiosyncratic returns with mean zero and variance $\Omega_{\epsilon}$

#### Latent factor <!-- {docsify-ignore} -->

when $f_{t+1}$ is latent and is to be estimated, the model is under-identified because any pair $(Z_t\Gamma^*,f_{t+1}^*)$ is as good as $(Z_{t}\Gamma,f_{t+1})$ where $\Gamma^{*}=\Gamma A \text{ and } f_{t+1}^{*}=A^{-1}f_{t+1}$ with $A$ being a $k \times k$ invertible matrix. 

Therefore, further restrictions on the parameters are needed in estimation.

> 如果任意旋转都可以得到 $\beta^*$ 以及对应的 $f^*_t$，那么则代表因子本身的意义并不清晰

This under-identification is well-known in the literature of principal component analysis–based methods of constructing factor-mimicking portfolios, IPCA also has to apply some constraints. 

It is worth noting that this does not apply to **affine transformations**. If $Z_t \Gamma$ is affine-transformed to $Z_{t}\Gamma^{*}=Z_{t}\Gamma A+C_{t}$, then, in general, there is no $f^*_{t+1}$ such that $Z_t\Gamma f_{t+1}= Z_t\Gamma^*f_{t+1}^*$

### Why affine instead of linear transformation

1. affine transformation is basically equal to linear transformation plus translation

linear: $y = Ax$

affine: $y = Ax + b$

> [!NOTE|Tips]
> affine transformation in *low dimension* is equal to linear transformation in *high dimension*
$$
y = Ax+b \Longrightarrow \begin{bmatrix}y\\1\end{bmatrix}=\begin{bmatrix}A&b\\\mathbf{0}&1\end{bmatrix}\begin{bmatrix}x\\1\end{bmatrix}
$$
> [【affines GIF】](https://pica.zhimg.com/50/v2-01d06795480b91a9bc1fa57ce5fd7009_720w.webp?source=1940ef5c)


so when $b$ is zero scalars, affine transformation is equal to linear transformation which is a special case of affine transformation

2. the test of the zero pricing error hypothesis can be conducted *meaningfully*

### Two types of pricing errors

#### Inside pricing error <!-- {docsify-ignore} -->

**核心含义**：whether the predictive power of a given set of firm characteristics can be rationalized by considering them as the base of the beta with respect to latent factors (usually less than characteristics)

> 因为要检验 $l$ 个公司特征能否由 $k$ 个因子解释，那么按照 APT 理论，这一部分的 $\alpha$ 就应该与 $k$ 个因子的 $\beta$ 正交。


- the $P_{it}$ is within the subspace spanned by $Z^*_t$ but **orthogonal** to $Z^*_t \Gamma$ when $l>k$

- the $P_{it}\delta_i$ can be viewed as **correct version** of IPCA to replace the term $Z_t \Gamma_{\alpha}$
  
- the inside-model pricing error can **always** be driven to zero if the number of factors k can be increased to the number of discovered return-predictive firm characteristics, which means the pricing error is meaningful only when $l$ is relatively greater than $k$

- because $P$ are *orthonormal basis*, thus $(P_{it}\delta_{i})^{\prime}P_{it}\delta_{i}=\delta_{i}^{\prime}\delta_{i}\equiv||\delta_{i}||^{2}.$

- When $k=l$, the $P_{it}\delta_i$ term drops out

> The same is true for IPCA, when $k=l$, $\Gamma_\beta$ is an invertible square matrix. The only solution to $\Gamma^{\prime}_\beta \Gamma_\alpha = 0$ is $\Gamma_\alpha = 0_k$


#### Outside pricing error [Beyond IPCA] <!-- {docsify-ignore} -->




<hr>



## Technical details





## Empirical results




panel的问题


inside error 是因为你知道是啥，是由模型内部决定的，但outside error不知道是啥

为什么k越大，inside error就越小，二者有什么关系？除了l-k的关系

是啥ijis

两个error之间的关系，有没有可能inside为0而outside不为0，或者反之

为什么要有panel AB 和 CD 两种检验方法，CD相当于对AB的拆解

PCA那块没怎么看懂，哪来的20个因子，因子不是估计出来的吗？


