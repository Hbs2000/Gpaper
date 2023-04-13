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
\Longrightarrow \ & w^* = \lambda \Sigma^{-1} \hat{\mu} - \gamma \Sigma^{-1} \bm{1}
\end{aligned}
$$

解得：
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

定义切点组合：
$$
w_{tan} = {\Sigma^{-1}\hat{\mu} \over \bm{1}^T \Sigma^{-1}\hat{\mu} }
$$

则原式变形为：
$$\begin{aligned}
w^* &= \lambda \Sigma^{-1} \hat{\mu} - \gamma \Sigma^{-1} \bm{1} \\ 
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

如此一来，二者之间非常明了的**一一对应的**关系跃然纸上，当我们以最大化样本内收益率为目标时，此时最大的收益率为：

$$
\mu_0 = \mu_{max} = \hat{\mu}^T w_{tan}
$$
因此 $\alpha_{\mu_0}=1$，最终解为：

$$
w^* = w_{tan} = {\Sigma^{-1}\hat{\mu} \over \bm{1}^T \Sigma^{-1}\hat{\mu} }
$$

也即我们常说的，**与夏普比率成正比的无约束解**。



