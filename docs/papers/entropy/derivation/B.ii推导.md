这里只写出根据Appendix E得到的Section II.B的pricing kernel的推导过程

The consumption growth process is
$$
log g_t=log g'+\gamma(B)v^{1/2}_{t-1}w_{gt}
$$

where $w_t$ is standard normal

Given a value of $b_1$, we use equation (24) to characterize the value function and substitute the result into the pricing kernel (17). 

The certainty equivalents needed for the recursion (24) are closely related to the cumulant generating functions of the relevant random variables. Consider an arbitrary random variable $y_{t+1}$ whose conditional cumulant generating function is $k_t(s; y) = log E_t(e^{sy_{t+1}})$. Then the log of the certainty equivalent (15) of $e^{a_t+b_t y_{t+1}}$ is
$$
log\mu_t(e^{a_t+b_t y_{t+1}})=a_t+k_t(\alpha b_t)/\alpha\tag{i}
$$
We use two kinds of cumulant generating functions below: for the standard normals we have $k_t(s; y) = s^2/2$.

We find the value function by guess-and-verify:

###### Guess. 
We guess a value function of the form
$$logu_t=logu+p(B)v^{1/2}w_{t}\tag{ii}$$
with parameters $(u, p)$ to be determined.
###### Compute certainty equivalent. 
Given our guess, $log(g_{t+1}u_{t+1})$is
$$
\begin{aligned}
log(g_{t+1}u_{t+1})&=log g_{t+1}+logu_{t+1}\\
&=(logg+\gamma(B)v^{1/2}w_{t+1})+(logu+p(B)v^{1/2}w_{t+1})\\
&=log(gu)+[\gamma(B)+p(B)]v^{1/2}w_{t+1}\\
&=log(gu)+[\gamma(B)+p(B)-\gamma_0-p_0]v^{1/2}w_{t+1}\\
&+(\gamma_0+p_0)v^{1/2}w_{t+1}
\end{aligned}
$$
由（i）得
$$
\begin{aligned}
log\mu_t(g_{t+1}u_{t+1})&=log(gu)+[\gamma(B)+p(B)-\gamma_0-p_0]v^{1/2}w_{t+1}\\
&+\frac{\alpha(\gamma_0+p_0)^2v}{2}
\end{aligned}
$$
由[[B. Models with Constant Variance#^b6f60b|（24）]]式
$$
\begin{aligned}
logu_t&=b_0+b_1log\mu_t(g_{t+1}u_{t+1})\\
&=b_0+b_1\{log(gu)+[\gamma(B)+p(B)-\gamma_0-p_0]v^{1/2}w_{t+1}\\ &+\frac{\alpha(\gamma_0+p_0)^2v}{2}\}\\
&=b_0+b_1[log(gu)+\frac{\alpha(\gamma_0+p_0)^2v}{2}]\\
&+b_1[\gamma(B)+p(B)-\gamma_0-p_0]v^{1/2}w_{t+1}
\end{aligned}\tag{iii}
$$
将（ii）($u_{t+1}$)与（iii）对比（$w_{t+1}$的系数相对应）得到
$$
p(B)B=b_1[\gamma(B)+p(B)-\gamma_0-p_0]
$$
令$B=b_1$，得到$\gamma_0+p_0=\gamma(b_1)$

$$
log(g_{t+1}u_{t+1})-log\mu_t(g_{t+1}u_{t+1})=\gamma(b_1)v^{1/2}w_{t+1}-\alpha/2[\gamma(b_1)]^2v
$$

对[[A. Preferences and Pricing Kernels#^ec0323|(17)]]式求导得
$$
\begin{aligned}
logm_{t,t+1}&=log\beta+(\rho-1)logg_{t+1}+(\alpha-\rho)[logu_{t+1}-log\mu_t(g_{t+1}u_{t+1})]\\
&=log\beta+(\rho-1)(logg+\gamma(B)v^{1/2}w_t)\\
&+(\alpha-\rho)\{\gamma(b_1)v^{1/2}w_{t+1}-\alpha/2[\gamma(b_1)]^2v\}\\
&=log\beta+(\rho-1)logg+(\alpha-\rho)(-\alpha/2[\gamma(b_1)]^2v)\\
&+[(\rho-1)\gamma(B)+(\alpha-\rho)\gamma(b_1)]v^{1/2}w_{t+1}\\
&=constant+[(\rho-1)\gamma(B)+(\alpha-\rho)\gamma(b_1)]v^{1/2}w_{t+1}
\end{aligned}
$$
