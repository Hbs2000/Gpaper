# Generalized Least Square

从名字可以看出，GLS 是 OLS 的拓展，主要用于处理 OLS 中残差**同方差** （homoskedasticity）和**序列不相关**（absence of serial correlation）不再成立时的情况。在这种情况下，OLS 估计量不再满足 BLUE（best linear unbiased estimator），而 GLS 估计量仍然满足 BLUE。

<hr>

对于常规的线性回归方程来说，如果其满足高斯-马尔可夫定理，则通过 OLS 得出的估计量为 BLUE。

$$
y = X\beta + \varepsilon 
$$

> [!NOTE|label:Gauss-Markov theorem]
> 在线性回归模型中，如果误差满足**零均值**，**同方差**且**互不相关**，则回归系数的最佳线性无偏估计量就是 OLS estimator。
$$
E(\varepsilon) = 0, \quad var(\varepsilon) = \bm{V} = \sigma^2 \bm{I}
$$
>
> 如果没有高斯-马尔可夫定理，最小二乘估计只是一种看上去合理且计算简便的算法。 ***高斯-马尔可夫定理从统计学的角度肯定了最小二乘法的合法性*** 。


而当 $var(\varepsilon) = \bm{V}$ 中存在异方差和序列相关时，通过 OLS 得出的估计量不再为 BLUE。

此时，由于 $\bm{V}$ 为对称非奇异矩阵，因此 $\bm{V}$ 可以被分解为：

$$
\bm{V} = \Sigma \Sigma^T
$$

将原本的回归方程改为：

$$
\Sigma^{-1}y=\Sigma^{-1}X\beta+\Sigma^{-1}\varepsilon
$$


定义：

$$
\begin{aligned}
\tilde{y}&=\Sigma^{-1}y \\
\tilde{X}&=\Sigma^{-1}X \\
\tilde{\varepsilon}&=\Sigma^{-1}{\varepsilon}
\end{aligned}
$$

则问题转化为：

$$
\tilde{y} = \tilde{X} \beta + \tilde{\varepsilon}
$$

则 GLS 估计量为，

$$
\begin{aligned}
\hat{\beta}_{GLS}& =\left(\tilde{X}^{T}\tilde{X}\right)^{-1}\tilde{X}^{\tau}\tilde{y}  \\
&=\left(X^\top V^{-1}X\right)^{-1}X^\top V^{-1}y
\end{aligned}
$$

此时，$\hat{\beta}_{GLS}$ 为 BLUE 估计量。

估计量对应的优化问题也发生了变化：

$$\begin{aligned}
\hat{\beta}_{OLS}&=\operatorname{arg}\min_{b}(y-Xb)^{\top}(y-Xb) \\
\hat{\beta}_{GLS}&=\arg\min\limits_{b}(y-Xb)^\top V^{-1}(y-Xb)
\end{aligned}$$

该优化问题也可以写成：

$$
\begin{aligned}
&(y-Xb)^\top V^{-1}(y-Xb) \\
=& \left[\Sigma^{-1}(y-Xb)\right]^\top\left[\Sigma^{-1}(y-Xb)\right] 
\end{aligned}
$$

## Weighted least squares

当 $\bm{V}$ 中仅存在异方差而没有序列相关时，GLS estimator 被称之为 WLS estimator，

此时：

$$

\bm{V} = 
\begin{pmatrix}
{\sigma_1^2} & {0} & {\cdots} & {0} \\
{0} & {\sigma_2^2} & {\cdots} & {0} \\
{\vdots} & {\vdots} & {\ddots} & {\vdots} \\ 
{0} & {0} & {\cdots} & {\sigma_n^2} 
\end{pmatrix}
$$

此时定义方差倒数为权重 $w_i = {1\over \sigma_i^2} $，则权重矩阵 $ \bm{V}^{-1} =  \bm{W}$ 为：

$$
\bm{W} = 
\begin{pmatrix}
{w_1} & {0} & {\cdots} & {0} \\
{0} & {w_2} & {\cdots} & {0} \\
{\vdots} & {\vdots} & {\ddots} & {\vdots} \\ 
{0} & {0} & {\cdots} & {w_n} 
\end{pmatrix}
$$

此时估计量变为：

$$
\hat{\beta}_{WLS} =\left(X^\top WX\right)^{-1}X^\top Wy
$$

权重是残差方差的倒数，这反映了对应observation的信息。如果observation的方差小，就代表含有更多的信息，因此权重更大，反之亦然。





