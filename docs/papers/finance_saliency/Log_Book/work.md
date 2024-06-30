# Frequency

## Methodology

Neuhierl and Varneskov (2021) 告诉我们，资产 $i$ 与 $M$ (market factor in the paper) 之间的协方差可分解到不同频率上得到；

$$
\begin{equation}
    \mathbf{C}_{iM}(\vartheta_1,\vartheta_2)\simeq\frac{2\pi}{T}\sum_{j=\vartheta_1}^{\vartheta_2}\Re(\mathbf{I}_{iM}(\lambda_j)),
\end{equation}
$$

其中，

$$
I_{iM}(\lambda_j)=\boldsymbol{w}_i(\lambda_j)\bar{\boldsymbol{w}}_M(\lambda_j), \qquad \mathbf{w}_i(\lambda_j)=\frac1{\sqrt{2\pi T}}\sum_{t=1}^T\tilde{r}_{i,t}e^{\mathrm{i}t\lambda},
$$

> [!WARNING|label:Problems]
> 这一协方差分解公式仅限于两两之间，在 Neuhierl and Varneskov (2021) 中，则是个股与某一因子的分解，很明显这一方法论有些问题，因为在分开考虑每一个因子的过程中，并没有体现出全局的信息，例如，在考虑个股与市场因子的协方差低频分解部分时，如果能够同时考虑其他因子，会得到更加准确的**与收益率相关的**频率信息。

***如何考虑其他因子？***

基于 $E(MR^e) = 0$，以及 $M_t = 1 - b'(f_t-E[f_t])$，有


$$\begin{aligned}
0' &= E[(1-b'(f_t-E[f_t]))R^{e \prime}]    \\
&= E[R^e]' - E[b'(f_t-E[f_t])R^{e \prime}] \\
&= E[R^e]' - E[b'(f_t-E[f_t])(R^e-E[R^e])'] \\
&= E[R^e]' - b'\Sigma_{f R^e}
\end{aligned}$$

得到：

$$
E[R^e]' = b'\Sigma_{f R^e}
$$

转置得：

$$
\begin{equation}
    E[R^e] = \Sigma_{f R^e}b
\end{equation}
$$

也就是说，风险价格 $b$ 是**资产超额收益率均值**回归到**资产与因子收益率协方差矩阵上**的回归系数。这一协方差矩阵包括了资产与所有因子 $f_t$ 两两之间的协方差。

具体来看，以资产数 (1,2) 为 2，因子数 (A,B,C) 为 3 为例：

$$
\left(  
\begin{matrix}
    E[R^e_1] \\ E[R^e_2]
\end{matrix}\right) = 
\left( \begin{matrix}
    \sigma_{1A} , \sigma_{1B}, \sigma_{1C} \\
    \sigma_{2A} , \sigma_{2B}, \sigma_{3C}
\end{matrix} \right) 
\left(  
\begin{matrix}
    b_A \\ b_B \\ b_C
\end{matrix}\right)
\\
\Longrightarrow E[f_1] = b_A \sigma_{1A} + b_B \sigma_{1B} + b_C \sigma_{1C}
$$

则，将每一个协方差分解到不同频率，则**均值可由不同频率表示**：

$$
\begin{aligned}
    E[R^e_1] &= b_{A} \sum_{j=\vartheta_1}^{\vartheta_2}\Re(\mathbf{I}_{1A}(\lambda_j)) + b_{B} \sum_{j=\vartheta_1}^{\vartheta_2}\Re(\mathbf{I}_{1B}(\lambda_j))+ b_{C} \sum_{j=\vartheta_1}^{\vartheta_2}\Re(\mathbf{I}_{1C}(\lambda_j)) \\    
    &= \sum_{j=\vartheta_1}^{\vartheta_2} \Re\left(b_{A}\mathbf{I}_{1A}(\lambda_j)+b_{B}\mathbf{I}_{1B}(\lambda_j)+b_{C}\mathbf{I}_{1C}(\lambda_j)\right)
\end{aligned}
$$

此时，**风险价格作为各个因子的权重，将资产收益率通过不同频率的实部表示出来**。接着在此基础上，可以进行低频或高频占比 sort，此时捕捉到的频率与资产收益率之间的关系，是综合了全部因子的结果。

## Empirical

### Setting

1. 基于 Neuhierl and Varneskov (2021)，关于协方差分解的方法论完全继承，区别在于将**风险价格 $b$ 作为权重**，因而纳入了多因子频率分解的体系。
2. 风险价格 $b$ 的估计，在这一步，只取估计系数显著的因子进入下一阶段频率分解

$$
    \hat{b} = \underset{b}{\argmin} \left\{(\bar{\mu}-\Sigma b)'(\bar{\mu}-\Sigma b) + \lambda_1|b|+ \lambda_2 b'b \right\}
$$

> 既然 $b$ 作为权重存在，那么就需要讨论一下 **正负** 的问题，如果两个因子估计系数相反，那么在频率上就会抵消，因此可以取绝对值处理，实证部分关于二者都做了实验。

3. 目前考虑因子为**Market**, **Value**, **Size**, **Long term reversal**, **Short term reversal**
