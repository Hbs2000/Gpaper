# Misalgnment of return model and risk model

业界无论是公募还是私募、无论是买方还是卖方，各家都有自有（proprietary）收益模型，而对于风险模型则一般使用现成的商业模型。*由于收益模型和风险模型中的因子不同*，造成了两个模型之间的错位。

> 按理说是一个值得研究的问题，为什么现有文献这么少？

## 收益模型

收益率模型的作用是**预测股票的收益率，从而获得超过基准的超额收益**。因此，开发收益率模型的目标就是找到能够预测股票收益率的变量，一般称之为：**Return predictors**。

> [!NOTE|label:预测变量与阿尔法因子]
> Return predictors 不可被称作阿尔法因子。从最基础的定价公式出发
$$
E[R_i^e]=\alpha_i+\boldsymbol{\beta}'_i\boldsymbol{\lambda}
$$
> 考虑以下例子：
>
> 1. 由于和收益率呈正相关，BM 常被拿来作为预测变量放在收益模型中。
> 2. 特质性波动率异象的收益率无法被定价模型所解释。因此 IVOL 也是一个优秀的预测变量。
>
> 一般来说，BM 是构建价值因子的变量，使用它构建的投资组合是价值因子，IVOL 是构建特质性波动率的变量，通过它构建的投资组合是特质性波动率异象。价值因子被称之为定价因子，而 IVOL 则被称之为异象因子。
> 
> 收益模型中的 predictor 既可以是异象变量（对应 $\alpha$），又可以是因子变量 （对应 $\boldsymbol{\beta}'_i\boldsymbol{\lambda}$）

## 风险模型

风险模型的目的并非解释资产收益率的截面差异，而是为了更加准确地计算资产协方差矩阵 $\Sigma$。

通过风险模型可以实现降维，方便地计算股票的协方差矩阵，并以此作为投资组合风险控制的依据。股票协方差矩阵和因子协方差矩阵的关系如下：

$$
\Sigma{=}\beta\Sigma_\lambda\beta^{\prime} + \Sigma_\varepsilon 
$$

其中 $\beta=[\beta_{1},\beta_{2},\cdots,\beta_{N}]^{\prime}$ 是 $N\times K$ 维因子暴露矩阵；$\Sigma,\Sigma_{\lambda},\Sigma_{\epsilon}$ 分别为股票的协方差矩阵，因子的协方差矩阵，以及随机扰动的协方差矩阵，一般假设股票收益率中的随机扰动相互独立，因此 $\Sigma_{\epsilon}$ 是对角阵。  

最常用的风险模型即为 Barra risk model。

## Misalignment

无论是风险模型还是收益率模型，其对收益的贡献都可以表示为：

$$
\begin{aligned}
    r &= \beta_R f_R + \varepsilon_R \\
    r &= \beta_A f_A + \varepsilon_A 
\end{aligned}
$$

下标 $R$ 表示风险模型，$A$ 表示收益率模型。进一步协方差计算如下：

$$
\Sigma = \beta_R \Sigma_R \beta'_R+\Sigma_{\varepsilon}
$$


相对基准的超额收益记为 $R^{\alpha}$，该超额收益可以被视作股票在收益预测变量上暴露的某个线性组合：

> 这是什么意思？

$$
R^{\alpha} = \beta_{A}w
$$

下标 $\alpha$ 表示收益模型，$\beta_{A}$ 为股票在收益变量上的暴露矩阵。
 
该超额收益可以被分解为两部分，一部分为 $R^{\alpha}$ 在由 $K$ 个风险因子构成的超平面内的投影，另一部分是垂直于该超平面的残差。

$$
\boldsymbol{R}^{\alpha}=\underbrace{\boldsymbol{\beta}_{R}\left(\boldsymbol{\beta}_{R}'\boldsymbol{\beta}_{R}\right)^{-1}\boldsymbol{\beta}_{R}'\boldsymbol{R}^{\alpha}}_{\text{hyperplane}}+\underbrace{\left(\boldsymbol{I}-\boldsymbol{\beta}_{R}\left(\boldsymbol{\beta}_{R}'\boldsymbol{\beta}_{R}\right)^{-1}\boldsymbol{\beta}_{R}'\right)\boldsymbol{R}^{\alpha}}_{\text{residual}}
$$


投资组合优化中最常见的目标函数是 Markowitz (1952) 均值方差模型：

$$
\max_{\boldsymbol{\omega}}(\boldsymbol{R}^{\alpha})'\omega-\frac{\zeta}{2}\omega'\Sigma\omega 
$$

无约束最优解为 $\omega^{\star}=\frac{1}{\zeta}\Sigma^{-1}R^{\alpha}$

> 为什么最优化的目标是超额收益率 alpha 而不是总收益率，只有优化总收益率时，后面的协方差矩阵才应该为个股协方差？

由于 $\Sigma = \beta_R \Sigma_R \beta'_R+\Sigma_{\varepsilon}$，根据 **Woodbury formula** $(A+UCV)^{-1}=A^{-1}-A^{-1}U(C^{-1}+VA^{-1}U)^{-1}VA^{-1}$，有：

$$
\begin{aligned}
    \Sigma^{-1}=\Sigma_s^{-1}-\Sigma_s^{-1}\beta_R(\Sigma_R^{-1}+\beta_R^{\prime}\Sigma_s^{-1}\beta_R)^{-1}\beta_R^{\prime}\Sigma_s^{-1}.
\end{aligned}
$$

由于个股特质性方差一样且互不相关：

$$
\begin{aligned}
    \Sigma^{-1}&=\Sigma_s^{-1}-\Sigma_s^{-1}\beta_R(\Sigma_R^{-1}+\beta_R^{\prime}\Sigma_s^{-1}\beta_R)^{-1}\beta_R^{\prime}\Sigma_s^{-1}. \\
    &= \frac{1}{\sigma_s^2}I-\frac{1}{\sigma_s^2}I\cdot\beta_R\left(\Sigma_R^{-1}+\beta_R^{\prime}\cdot\frac{1}{\sigma_s^2}I\cdot\beta_R\right)^{-1}\cdot\beta_R^{\prime}\cdot\frac{1}{\sigma_s^2}I\\
    &= \frac{1}{\sigma_s^2} \left( I - \beta_R\left(\sigma_s^2\Sigma_R^{-1}+\beta_R^{\prime}\cdot\beta_R\right)^{-1}\cdot\beta_R\right)
\end{aligned}
$$

定义 $\boldsymbol{R}_{R}^{\alpha}\equiv\boldsymbol{\beta}_{R}(\boldsymbol{\beta}_{R}^{\prime}\boldsymbol{\beta}_{R})^{-1}\boldsymbol{\beta}_{R}^{\prime}\boldsymbol{R}^{\alpha},\boldsymbol{R}_{\perp}^{\alpha}\equiv(\boldsymbol{I}-\boldsymbol{\beta}_{R}\left(\boldsymbol{\beta}_{R}^{\prime}\boldsymbol{\beta}_{R}\right)^{-1}\boldsymbol{\beta}_{R}^{\prime})\boldsymbol{R}^{\alpha}$，因此，有：

$$
\begin{aligned}
    \omega^\star& = \frac{1}{\zeta\sigma_s^2} \left( I - \beta_R\left(\sigma_s^2\Sigma_R^{-1}+\beta_R^{\prime}\cdot\beta_R\right)^{-1}\cdot\beta_R\right) \boldsymbol{R}^{\alpha}  \\
    &=\frac{1}{\zeta\sigma_s^2}\left(  \boldsymbol{R}_\perp^\alpha + \boldsymbol{R}_R^\alpha -\boldsymbol{\beta}_R\left(\boldsymbol{\beta}_R^\prime\boldsymbol{\beta}_R+\sigma_s^2\boldsymbol{\Sigma}_R^{-1}\right)^{-1}\boldsymbol{\beta}_R^\prime\boldsymbol{R}_R^\alpha  \right) \\
    &= \frac{1}{\zeta\sigma_s^2} \left(  \boldsymbol{R}_\perp^\alpha + \left(\boldsymbol{I}-\boldsymbol{\beta}_R\left(\boldsymbol{\beta}_R^\prime\boldsymbol{\beta}_R+\sigma_s^2\boldsymbol{\Sigma}_R^{-1}\right)^{-1}\boldsymbol{\beta}_R^\prime\right)\boldsymbol{R}_R^\alpha  \right) \\
    &=\frac{1}{\zeta\sigma_s^2}\boldsymbol{R}_\perp^\alpha+\frac{1}{\zeta\sigma_s^2}\left(\boldsymbol{I}-\boldsymbol{\beta}_R\left(\boldsymbol{\beta}_R^\prime\boldsymbol{\beta}_R+\sigma_s^2\boldsymbol{\Sigma}_R^{-1}\right)^{-1}\boldsymbol{\beta}_R^\prime\right)\boldsymbol{R}_R^\alpha
\end{aligned}
$$


