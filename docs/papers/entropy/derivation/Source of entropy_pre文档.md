dynamics指的是时间依赖性，是衡量熵在不同时间范围上的变化的指标

transparent loglinear approximations

tension between entropy, which should be ==large enough== to account for observed excess returns；and time dependence, which should be ==small enough== to account for [[mean yield spreads]].

[[Representative Agents Theory]]
两类Representative Agent model：
1. 基于[[recursive preference]]（递归偏好）
2. 基于[[habits contributing prominently]]
这是两种 generate 真实资产价格和收益的方法，但他们的机制完全不同。他们通常被认为是可替代的，这是真的吗？

基于[[pricing kernel]]的两个metrics（指标）的==意义==
summarize（总结）资产定价模型的properties（性质）
1. entropy measures pricing kernel的散度（确定超额收益的上限）
##### Denote
(true) probability of the state at date t + 1 conditional on the state at date t by $p_{t,t+1} = p(x_{t+1} | x_t)$. $p_{t,t+n} = \prod^n_{j=1}p_{t+j-1,t+j}=\prod^n_{j=1}p(x_{t+j}|x_{t+j-1})$. $p^*_{t,t+n}$ is the analogous risk-adjusted probability. The ==relative entropy of the risk-adjusted distribution== is then
$$
L_t(p^*_{t,t+n}/p_{t,t+n})=-E_tlog(p^*_{t,t+n}/p_{t,t+n})
$$
where $E_t$ is the conditional expectation based on the true distribution.([[Kullback–Leibler divergence]])

We associate large risk premiums with large differences between true and risk-adjusted probabilities.
Two ways to capture this difference
- log-likelihood ratio
- variability in $p^*_{t,t+n}/p_{t,t+n}$
    由$E_t(p^*_{t,t+n}/p_{t,t+n})=1$
$$
L_t(p^*_{t,t+n}/p_{t,t+n})=logE_t(p^*_{t,t+n}/p_{t,t+n})-E_tlog(p^*_{t,t+n}/p_{t,t+n})\tag{1}
$$
entropy is nonnegative and increases with variability

We think the concept of entropy is useful here because of its properties. It is connected to excess returns on assets and real bond yields in a convenient way.

#### Entropy over Short and Long Horizons
Entropy, suitably defined, supplies an upper bound on mean excess returns and a measure of the dynamics of the pricing kernel.
两个边界（Hansen-Jagannathan (1991) bound）都基于是资产定价理论中的基本结果:在无套利的环境中,有一个正的随机变量，
$$E_t(m_{t+n}r_{t+n})=1\tag{2}$$
$m_{t,t+n}$ is the pricing kernel over the period $t$ to $t + n$ 
$r_{t,t+n}$ is the gross return on a traded asset over the same period.
Both can be decomposed into one-period components:
- $m_{t,t+n} = \prod^n_{j=1}m_{t+j-1.t+j}$ 
- $r_{t,t+n} = \prod^n_{j=1}r_{t+j-1,t+j}$ 

##### Conditional entropy
$$
L_t(m_{t,t+n})=logE_tm_{t,t+n}-E_tlog~m_{t,t+n}\tag{3}
$$
using the relation between the pricing kernel and conditional probabilities: $m_{t,t+n} = q^n_t p^∗_{t,t+n}/p_{t,t+n}$, where $q^n_t = E_tm_{t,t+n}$ is the price of an n-period bond
$$
\frac{\pi^*}{\pi}=\frac{m}{Em}
$$

Mean conditional entropy is
$$
EL_t(m_{t,t+n})=ElogE_tm_{t,t+n}-Elog~m_{t,t+n}\tag{a}
$$
where $E$ is the expectation based on the ==stationary distribution.==

##### entropy
scale this by the time horizon n, we have mean conditional entropy per period:
$$
I(n)=\frac{1}{n}EL_t(m_{t,t+n})\tag{4}
$$
[We refer to this simply as entropy from here on.]

We develop this definition of entropy in two directions, the first focusing on its value over one period, the second on how it varies with time horizon n.
1. we refer to as the entropy bound, connects one-period entropy to one-period excess returns:
$$
I(1)=EL_t(m_{t,t+1}) \geq E(log~r_{t,t+1}-log~r^1_{t,t+1})\tag{5}
$$
    where $r^1_{t,t+1} = \frac{1}{q^1_t}$,

![[（5）式推导]]


（iii）implies the upper bound of expected log return, the log return with the highest mean is, evidently, $log r_{t,t+n} =-logm_{t,t+n}$

$$
L_t(m_{t,t+1}) \geq E_tlogr_{t+1}-logr^1_{t,t+1}\tag{7}
$$
![[（7）式推导]]

take the expectation of both sides of (7) to produce the entropy bound (5).

The relation between one-period entropy and the conditional distribution of $logm_{t,t+1}$ is captured by its cumulant generating function and cumulants. 

The conditional cumulant generating function of $logm_{t,t+1}$ is the log of the moment generating function.
Conditioning is indicated by the subscript t. 
$$
k_t(s)=logE_t(e^{slogm_{t,t+1}})\tag{b}
$$
it has the power series expansion (c) over some suitable range of s.
$$
k_t(s)=\sum^\infty_{j=1}\kappa_{jt}\frac{s^j}{j!}\tag{c}
$$
The conditional cumulant $\kappa_{jt}$ is the jth derivative of $k_t(s)$ at s = 0; $\kappa_{1t}$ is the mean, $\kappa_{2t}$ is the variance, and so on. The third and fourth cumulants capture skewness and excess kurtosis, respectively.

In general we have
$$
\begin{aligned}
L_t(m_{t,t+1})&=k_t(1)-\kappa_{1t}\\
&=\underbrace{\kappa_{2t}\frac{logm_{t,t+1}}{2!}}_{normal~term}+\underbrace{\kappa_{3t}\frac{logm_{t,t+1}}{3!}+ \cdots}_{nonnormal ~terms}
\end{aligned}\tag{8}
$$
![[（8）式推导]]

If the conditional distribution of $logm_{t,t+1}$ is normal, then high-order cumulants (those of order j ≥ 3) are zero. 

We define horizon dependence as the difference in entropy over horizons of n and one, respectively:(characterize the dynamics of the pricing kernel)
$$
H(n)=I(n)-I(1)=\frac{1}{n}EL_t(m_{t,t+n})-EL_t(m_{t,t+1})\tag{9}
$$
when one-period pricing kernels $m_{t,t+1}$ are iid,
$$
EL_t(m_{t,t+n})=nEL_t(m_{t,t+1})\tag{c}
$$

This is a generalization of a well-known property of random walks: the variance is proportional to the time interval. As a result, entropy $I(n)$ is the same for all n and horizon dependence is zero.

In other cases, horizon dependence reflects ==departures from the iid case==, and in this sense is a measure of the ==pricing kernel’s dynamics==.
It captures not only the ==autocorrelation== of the log pricing
kernel, but ==variations== in all aspects of the conditional distribution. 

In a stationary environment, conditional entropy over n periods is
$$
\begin{aligned}
L_t(m_{t,t+n})&=logE_tm_{t,t+n}-E_tlog~m_{t,t+n}\\
&=logq^n_t-E_t\sum^n_{j=1}log~m_{t+j-1,t+j}
\end{aligned}\tag{d}
$$
so Entropy (4) is therefore
$$
I(n)=\frac{1}{n}Elogq^n_t-Elogm_{t,t+1}\tag{e}
$$
Bond yields are related to prices by $y^n_t =−\frac{1}{n} log q^n_t$.(A.1)
Therefore, horizon dependence is related to mean yield spreads by
$$
H(n)=-E(y^n_t-y^1_t)\tag{f}
$$
In words: horizon dependence is negative if the mean yield curve is increasing, positive if it is decreasing, and zero if it is flat. Since mean forward rates and returns are closely related to mean yields, we can express horizon dependence with them too.(A1)

Observed excess returns tell us that one-period entropy is probably greater than 1% monthly

Observed excess returns tell us that one-period entropy is probably greater than 1% monthly. Observed bond yields tell us that horizon dependence is smaller, probably less than 0.1% at observable time horizons.(由实证数据得到horizon dependence应该很小，但不会为0，为0的话就是RW)

#### An Example: The Vasicek Model
The pricing kernel is
$$
\begin{aligned}
logm_{t,t+1}&=logm+\sum^\infty_{j=0}\alpha_jw_{t+1-j}\\
&=logm+\alpha(B)w_{t+1}
\end{aligned}\tag{12}
$$
The solution is most easily expressed in terms of forward rates, which are connected to bond prices.
Forward rates in this model are
$$
-f^n_t = log m+ k(A_n) + [\alpha(B)/B^{n+1}]_+w_t \tag{13}
$$
for n ≥ 0 and $A_n =\sum^n_{j=0} \alpha_j$.
![[(13)推导]]

Mean forward rates are therefore 
$$-E( f^n_t ) = log m+ k(A_n)$$

$y^n_t =\frac{1}{n}\sum^n_{j=1}f^{j-1}_t$,
so mean yields: $-Ey^{n+1}_t =logm+\frac{1}{n}\sum^n_{j=1}k(A_{j-1})$

In this setting, the initial coefficient $(a_0)$ governs one-period entropy and the others $(a_j ~for ~j \geq 1)$ combine with it to govern horizon dependence.

Entropy is
$$
I(n) = \frac{1}{n}EL_t(m_{t,t+n}) = \frac{1}{n}\sum^n_{j=1}k(A_{j-1})
$$
for any positive time horizon n. Horizon dependence is therefore
$$
H(n) = I(n) - I(1) = \frac{1}{n}\sum^n_{j=1}[k(A_{j-1})-k(A_0)]
$$

Here we see the role of dynamics. In the iid case(m iid，即RW) $(a_j = 0 ~for ~j \geq 1)$, $A_j = A_0 = a_0$ for all j and horizon dependence is zero at all horizons. Otherwise horizon dependence depends on the relative magnitudes of $k(A_{j−1})$ and $k(A_0)$

We also see the role of the distribution of $w_t$. Our benchmarks suggest $k(A_0)$ is big (at least 0.0100 = 1% monthly/ 12.7% yearly) and $k(A_{j−1}) − k(A_0)$ is small (no larger than 0.0010 = 0.1% on average). The latter requires, in practice, small differences between $A_0$ and $A_{j−1}$, and hence small values of $a_j$.

We make $logm_{t,t+1}$ an ARMA(1,1) process. Its three parameters are $(a_0, a_1,\varphi)$, with $a_0 > 0$ and $|\varphi| < 1$ (to ensure square summability). They imply moving average coefficients $a_{j+1} = \varphi a_j$ for $j \geq 1$. This leads to an AR(1) for the short rate.
注释：
1. 为什么$a_0=\nu^{\frac{1}{2}},~a_1=(\varphi-\theta)\nu^{\frac{1}{2}}$
由（12）式
$$
logm_{t,t+1}=logm+\alpha(B)w_{t+1}
$$
令 $X_{t+1}=logm_{t,t+1}-logm$, (12)式变为
$$
\begin{aligned}
X_{t+1}&=\alpha(B)w_{t+1}\\
&=(a_0+a_1+\cdots)w_{t+1}
\end{aligned}
$$
又由$X_{t+1}$是ARMA(1,1)
$$
\begin{aligned}
(1-\varphi B)X_{t+1}&=(1-\theta B)\nu^{\frac{1}{2}}w_{t+1}\\
X_{t+1}&=\frac{1-\theta B}{1-\varphi B}\nu^{\frac{1}{2}}w_{t+1}\\
X_{t+1}&=[1-(\varphi+\theta)B-\varphi(\varphi+\theta)B^2+\cdots]\nu^{\frac{1}{2}}w_{t+1}\\
\end{aligned}
$$
所以有 $a_0=\nu^{\frac{1}{2}},~a_1=(\varphi-\theta)\nu^{\frac{1}{2}}$。($a_j=\varphi a_{j-1}$ for $j > 1$)
2. 为什么short rate 是AR(1)
The short rate is $log r^1_{t,t+1} = f^0_t = y^1_t$ ，由（13）式
$$
\begin{aligned}
-f^0_t &= log m+ k(A_0) + [\alpha(B)/B]_+w_t\\
-f^0_t - log m- k(A_0)&=(a_1+\cdots)w_t\\
&=a_1(1+\varphi+\varphi^2+\cdots)w_t\\
(1-\varphi B)[-f^0_t - log m- k(A_0)]&=a_1w_t
\end{aligned}
$$
so short rate is AR(1)，and $Var(logr^1_{t,t+1}) = \frac{a^2_1}{(1 -\varphi^2)}$.

We choose $\varphi$ and $a_1$ to match the autocorrelation and variance of the short rate and $a_0$ to match the mean spread between 1-month and 10-year bonds. The result is a statistical model of the pricing kernel that captures some of its central features.

We set $\varphi = 0.85$, an estimate of the monthly autocorrelation of the real short rate reported by Chernov and Mueller (2012). Chernov and Mueller report a standard deviation of (0.02/12; 2% annually), which implies 
 $|a_1|= 0.878 × 10^{−3}$. Neither of these numbers depends on the distribution of $w_t$.
 注释：$a_1$计算结果检查
 ![[Pasted image 20221214211940.png]]

We choose $a_0$ to match the mean yield spread on the 10-year bond. This calculation depends on the distribution of $w_t$ through the cumulant generating function $k(s)$. We do this here for the ==normal case==, where $k(s) = \frac{s^2}{2}$, but the calculation is easily repeated for other distributions. If the yield spread is $E(y^{120} - y^1) = 0.001$==(Typo)==, this implies $a_0 = 0.1837$ and $a_1 < 0$. We can reproduce a negative yield spread of similar magnitude by making $a_1$ positive.
注释：怎么计算$a_0$以及对它的计算结果的检查
由之前的（f）式
$$
\begin{aligned}
H(n)&=-E(y^n_t-y^1_t)\\
&= \frac{1}{n}\sum^n_{j=1}[k(A_{j-1})-k(A_0)]
\end{aligned}
$$
所以有
$$
E(y^n_t-y^1_t) = \frac{1}{n}\sum^n_{j=1}[k(A_0)-k(A_{j-1})]
$$
![[Pasted image 20221214220744.png]]

PS: $a_1 > 0$ 经验证不符合条件
![[Pasted image 20221214223052.png]]
The configuration of moving average coefficients, with $a_0$ much larger than the others($a_0 \gg a_1$), means that ==the pricing kernel is only modestly different from white noise.== 

Stated in our terms: one-period entropy is large relative to horizon dependence. We see that in Figure 2. The dotted line in the middle is our estimated 0.0100 lower bound for one-period entropy. The two thick lines at the top are entropy for the two versions of the model.
1. The dashed one([[短横线表示的那条]]) is associated with negative mean yield spreads. We see that entropy rises (slightly) with the horizon. 
2. The solid line(实线表示的那条) below it is associated with positive mean yield spreads, which result in a modest decline in entropy with maturity.
The dotted lines around them are the horizon dependence bounds: one-period entropy plus and minus 0.0010. The models hit the bounds by construction.
![[Pasted image 20221214225729.png]]

The model also provides a clear illustration of long-horizon analysis. The
state here is the infinite history of innovations: $x_t = (w_t,w_{t−1},w_{t−2}, \dots)$
. Suppose $A_\infty=\alpha(1)=\underset{n \rightarrow \infty}{lim}\sum^n_{j=0}A_j$ exist, then the principal eigenvalue $\lambda$ and eigenfunction $e_t$ are
$$
log\lambda=logm+k(A_\infty)
$$
$$
loge_t=\sum^n_{j=0}(A_\infty-A_j)w_{t-j}
$$
Long-horizon entropy is $I(\infty) = k(A_\infty)$.

#### [[A. Preferences and Pricing Kernels]]

#### [[B. Models with Constant Variance]]

#### [[C. Models with Stochastic Variance]]









