In the models of the previous section, all of the variability in the distribution of the log pricing kernel is in its conditional mean. Here we consider examples proposed by Bansal and Yaron (2004, Case II) and Campbell and Cochrane (1999) that have variability in the conditional variance as well. They illustrate in different ways how variation in the conditional mean and variance can interact in generating entropy and horizon dependence.
One perspective on the conditional variance comes from recursive utility.
The Bansal–Yaron (2004, Case II) model is based on the bivariate consumption growth process:
$$
log g_t=logg+\gamma(B)v^{1/2}_{t-1}w_{gt}
$$
$$
v_t=v+v(B)w_{vt}
$$
where $w_{gt}$ and $w_{vt}$ are independent iid standard normal random variables. 
The first equation governs movements in the conditional mean of log consumption growth, the second governs movements in the conditional variance.

This linear volatility process is analytically convenient, but it implies that $v_t$ is normal and therefore negative in some states. We think of it as an approximation to a censored process $v_t = max{0,v_t}$. We show in Appendix G that, if the true conditional variance process is $v_t$, then an approximation based on (25) is reasonably accurate for the numerical examples reported later, where the stationary probability that vt is negative is small.
With this process for consumption growth and the loglinear approximation
(24), the Bansal–Yaron pricing kernel is
$$
\begin{aligned}
logm_{t,t+1}&=constant+[(\rho-1)\gamma(B)+(\alpha-\rho)\gamma(b_1)]v^{1/2}_tw_{gt+1}\\
&+(α − ρ)(α/2)γ(b_1)^2[b_1ν(b_1) − ν(B)B]w_{vt+1}
\end{aligned}
$$
The coefficients on the consumption growth innovation $w_{gt}$ now vary with $v_t$, but they are otherwise the same as before. The volatility innovation $w_{vt}$ is new. Its coefficients depend on the dynamics of volatility (represented by $v(b_1)$), the dynamics of consumption growth ($γ(b_1)$), and recursive
preferences ($(α − ρ)$). One-period conditional entropy is
$$
L_t(m_{t+1}) = [(ρ − 1)γ_0 + (α − ρ)γ(b_1)]^2v_t/2 + (α − ρ)^2(α/2)^2γ(b_1)^4[b_1ν(b_1)]^2/2
$$
which now varies with $v_t$. One-period entropy is the same with $v_t$ replaced by its mean v, because the log pricing kernel is linear in vt.
The pricing kernel looks like a two-shock Vasicek model, but the interaction between the conditional variance and consumption growth innovations gives it a different form. The pricing kernel can be expressed as
$$
logm_{t,t+1}=logm+a_g(B)(v_t/v)^{1/2}w_{gt+1}+a_v(B)w_{vt+1}
$$
with
$$
a_g(B) = (ρ − 1)γ(B) + (α − ρ)γ(b_1)
$$
$$
a_v(B) = (α − ρ)(α/2)γ(b_1)^2[b_1ν(b_1) − ν(B)B]
$$
In our examples, consumption growth innovations lead to positive horizon dependence, just as in the previous section. Variance innovations lead to negative horizon dependence, the result of the different signs of the initial and subsequent moving average coefficients in $a_v(B)$. The overall impact on horizon dependence depends on the relative magnitudes of the two effects and the nonlinear interaction between the consumption growth and conditional variance processes; see Appendix F.
We see the result in the first two columns of Table III. We follow Bansal
and Yaron (2004) in using an AR(1) volatility process, so that $v_{j+1} = \varphi_vv_ j$ for j ≥ 1. With their parameter values (column (1)), the stationary distribution of $v_t$ is normal with mean $v = 0.0099^2 = 9.8 × 10^{−5}$ and standard deviation $v_0/(1 − \varphi^2_v )^{1/2} = 1.4 × 10^{−5}$. The zero bound is therefore almost seven standard deviations away from the mean. The impact of the stochastic variance on entropy and horizon dependence is small. Relative to the constant variance case(column (2) of Table II), one-period entropy rises from 0.0214 to 0.0218 and 120-month horizon dependence from 0.0011 to 0.0012. This suggests that horizon dependence is dominated, with these parameter values, by the dynamics of consumption growth. The increase in horizon dependence over the constant variance case indicates that nonlinear interactions between the two processes are quantitatively significant