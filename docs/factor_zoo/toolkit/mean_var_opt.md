# Mean Variance Optimization

Formally, 
$$\begin{aligned}
\underset{w}{min} \quad & {1\over 2} w^T \Sigma w \\
\text{s.t. } & \bm{1}^T w = 1\\
& w^T \hat{\mu} = \mu_0
\end{aligned}
$$

Form the Lagrangian:
$$
\underset{w,\lambda,\gamma}{min} \quad {1\over 2} w^T \Sigma w + \lambda(\mu_0-w^T \hat{\mu})+\gamma(1-\bm{1}^T w)
$$

对 $w$ 求导，
$$\begin{aligned}
& \Sigma w - \lambda \hat{\mu} - \gamma \bm{1} = 0 \\
\Longrightarrow \ & w^* = \lambda \Sigma^{-1} \hat{\mu} + \gamma \Sigma^{-1} \bm{1}
\end{aligned}
$$

代入约束条件解得：
$$\begin{aligned}
\lambda = {\bm{1}^T\Sigma^{-1}\bm{1} \mu_0 - \hat{\mu}^T \Sigma^{-1}\bm{1} \over \bm{1}^T\Sigma^{-1}\bm{1} \hat{\mu}^T\Sigma^{-1}\mu - (\hat{\mu}^T \Sigma^{-1}\bm{1})^2 } \\
\gamma = {\hat{\mu}^T\Sigma^{-1}\hat{\mu} - \hat{\mu}^T \Sigma^{-1}\bm{1} \mu_0 \over \bm{1}^T\Sigma^{-1}\bm{1} \hat{\mu}^T\Sigma^{-1}\hat{\mu} - (\hat{\mu}^T \Sigma^{-1}\bm{1})^2 }
\end{aligned}
$$

当不限制均值约束，而仅仅最小化方差时：
$$\begin{aligned}
\underset{w}{min} \quad & {1\over 2} w^T \Sigma w \\
\text{s.t. } & \bm{1}^T w = 1
\end{aligned}
$$

解得最小方差组合权重为：
$$
w_{var} = {\Sigma^{-1}\bm{1} \over \bm{1}^T \Sigma^{-1}\bm{1} }
$$

**定义**切点组合：
$$
w_{tan} = {\Sigma^{-1}\hat{\mu} \over \bm{1}^T \Sigma^{-1}\hat{\mu} }
$$

<hr>

<div  class = 'centerwords'>

**变形1**
</div>

则原式变形为：
$$\begin{aligned}
w^* &= \lambda \Sigma^{-1} \hat{\mu} + \gamma \Sigma^{-1} \bm{1} \\ 
&= \lambda \bm{1}^T \Sigma^{-1}\hat{\mu}{\Sigma^{-1}\hat{\mu} \over \bm{1}^T \Sigma^{-1}\hat{\mu} } + \gamma \bm{1}^T \Sigma^{-1}\bm{1} {\Sigma^{-1}\bm{1} \over \bm{1}^T \Sigma^{-1}\bm{1} } \\
&= \alpha_{\mu_0}w_{tan}+(1-\alpha_{\mu_0})w_{var} \\
\text{suppose} & \quad \alpha_{\mu_0} = \lambda \bm{1}^T \Sigma^{-1}\hat{\mu} \\
\text{obvious} & \quad \lambda \bm{1}^T \Sigma^{-1}\hat{\mu} + \gamma \bm{1}^T \Sigma^{-1}\bm{1} = 1 
\end{aligned}$$

这代表任何组合均可由**最小方差组合**和**切点组合**线性表示【**两基金分离定理**】。

同时我们发现，通过这种表达，权重项中与目标收益率 $\mu_0$ 有关的项**只有** $\alpha_{\mu_0}$。

进一步，将 $\alpha_{\mu_0}$ 展开得到：

$$\begin{aligned}
\alpha_{\mu_0} &= {\bm{1}^T\Sigma^{-1}\bm{1} \mu_0 - \hat{\mu}^T \Sigma^{-1}\bm{1} \over \bm{1}^T\Sigma^{-1}\bm{1} \hat{\mu}^T\Sigma^{-1}\hat{\mu}- (\hat{\mu}^T \Sigma^{-1}\bm{1})^2 } \bm{1}^T \Sigma^{-1}\hat{\mu} \\
&= { \mu_0 - \hat{\mu}^T w_{var} \over  \hat{\mu}^T\Sigma^{-1}\hat{\mu}- \hat{\mu}^T w_{var}\hat{\mu}^T \Sigma^{-1}\bm{1} } \bm{1}^T \Sigma^{-1}\hat{\mu} \\
&= { \mu_0 - \hat{\mu}^T w_{var} \over  \hat{\mu}^T w_{tan} - \hat{\mu}^T w_{var}}
\end{aligned}$$

如此一来，$\mu_0$ 和 $\alpha_{\mu_0}$ 之间非常明了的**一一对应的**关系跃然纸上，当我们选择目标收益率 $\mu_0$ 来最大化样本内夏普比率时，此时一定会得到切点组合对应的收益率：

$$
\mu_0 = \mu_{tan} = \hat{\mu}^T w_{tan}
$$
因此 $\alpha_{\mu_0}=1$，最终解为：

$$
w^* = w_{tan} = {\Sigma^{-1}\hat{\mu} \over \bm{1}^T \Sigma^{-1}\hat{\mu} }
$$

也即我们常说的，**与夏普比率成正比的无约束解**。

因为是完全通过样本内得出的最优解，所以有严重的过拟合问题。在实际操作中，可以先通过样本内求得有效前沿，第二步通过样本外数据得到最优组合。

<hr>

<div  class = 'centerwords'>

变形2
</div>

当放松**权重条件**【即权重相加为1】：
$$\begin{aligned}
w^* &=  \lambda \Sigma^{-1} \hat{\mu} + \gamma \Sigma^{-1} \bm{1} \\
&= \Sigma^{-1} \hat{\mu} + {\gamma \over \lambda} \Sigma^{-1} \bm{1} \\
&= \Sigma^{-1} \left( \hat{\mu} + {\gamma \over \lambda} \bm{1} \right) \\
&= \Sigma^{-1} \left( \hat{\mu} + \lambda_0 \bm{1} \right)
\end{aligned}$$

此时：
$$\begin{aligned}
\lambda_0 &= {\gamma \over \lambda} \\ 
&= {\hat{\mu}^T\Sigma^{-1}\hat{\mu} - \hat{\mu}^T \Sigma^{-1}\bm{1} \mu_0 \over \bm{1}^T\Sigma^{-1}\bm{1} \mu_0 - \hat{\mu}^T \Sigma^{-1}\bm{1}}
\end{aligned}$$

因此，$\lambda_0$ 和 $\mu_0$ 之间也存在**一一对应**的关系。

$$\begin{aligned}
\lambda_0 \in [0,+\infty)  \Rightarrow & \mu_0  \in \left( {\hat{\mu}^T  \hat{\Sigma}^{-1} \bm{1} \over \bm{1}^T  \hat{\Sigma} ^{-1} \bm{1}},\ {\hat{\mu}^T \hat{\Sigma}^{-1} \mu \over \hat{\mu}^T  \hat{\Sigma}^{-1} \bm{1}} \right] \\
\Longrightarrow & \mu_0 \in \left( \hat{\mu}^T w_{var}, \ \hat{\mu}^T w_{tan} \right]
\end{aligned}$$

同样地，当最大化样本内 $\mu_0$ 为目标时，解得 $\lambda_0=0$。

但是，在这种变形下，出现了另一种解释：**收缩**【Shrinkage】。

$\lambda_0$ 是 $\mu_0$ 的递减函数，当 $\mu_0$ 大时，$\lambda_0$ 小，而当 $\mu_0$ 小时，相对来说 $\lambda_0$ 会大。这也代表着一种收缩，但不同于传统的Shinkage向0收缩，而是**向截面均值收缩**。


> [!NOTE]
> 二者一一对应的关系有两种理解。
> 
> （1）之所以是由 $\lambda_0$ 的取值范围推出 $\mu_0$ 的取值范围，是因为当 $\lambda_0$ 的取值小于 0 时，就不会起到收缩的效果，而是**会极化权重**【使得小权重趋于零】，因此，也就可以理解为，当 $\mu_0$ 的取值范围如上时，才有收缩的作用。
> 
> （2）在变形2这种表达下，$\lambda_0$ 的取值范围也代表我们并不认为 $\mu_0$ 会超过切点组合收益率。因为从夏普比率的角度来看，切点组合就是最优夏普比率，已经代表了最严重的过拟合，样本外的夏普比率不会高于这一点。






