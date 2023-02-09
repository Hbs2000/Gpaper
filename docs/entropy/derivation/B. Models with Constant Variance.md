We derive specific pricing kernels for each of these preferences based on loglinear processes for consumption growth and, for habits, the relation between the habit and consumption. 
When the pricing kernels are not already loglinear, we use loglinear approximations. The resulting pricing kernels have the same form as the Vasicek model. We use normal innovations in our numerical
examples to focus attention on the models’ dynamics, but consider other distributions at some length in Section II.D. Parameters are representative numbers from the literature chosen to illustrate the impact of preferences on entropy and horizon dependence.

对$g_t$（consumption growth）用loglinear近似表示
The primary input to the pricing kernels of these models is a consumption growth process. We use the loglinear process

$$
log g_t=logg+\gamma(B)v^{1/2}w_t\tag{23}
$$

^5dbea3

where $\gamma_0 = 1$, $\sum_j \gamma^2_j < \infty$, and innovations $w_t$ are iid with mean zero, variance one, and cumulant generating function $k(s)$. With normal innovations, $k(s) = \frac{s^2}{2}$.

With power utility [[A. Preferences and Pricing Kernels#^b63871|(18)]] and the loglinear consumption growth process (23), （即对(18)取log后再用(23)对$log g_{t+1}$进行代换）the pricing kernel takes the form
$$
logm_{t,t+1} = constant + (\rho - 1)\gamma(B)v^{1/2}w_{t+1}
$$
Here the moving average coefficients ($\alpha_j$ in Vasicek notation) are proportional to those of the consumption growth process: 
$$
\alpha(B) = (\rho - 1)\gamma(B)v^{1/2}\tag{B.i}
$$
so 
$$\alpha_j =(\rho - 1)\gamma_jv^{1/2}~ for ~all ~j \geq 0 $$The infinite sum is $A_\infty = \alpha(1) = (\rho - 1)\gamma(1)v^{1/2}$.

With recursive utility, we derive the pricing kernel from a loglinear approximation of [[A. Preferences and Pricing Kernels#^e94c19|(16)]],
$$
logu_t \approx b_0+b_1log\mu_t(g_{t+1}u_{t+1})\tag{24}
$$

^b6f60b

a linear approximation of $log u_t$ in $log\mu_t$ around the point $log\mu_t = log\mu$. See Hansen, Heaton, and Li (2008, Section III). 
[[(24)式推导]]

This is exact when $\rho = 0$, in which case $b_0 = 0$? and $b_1 = \beta$, the approximation used to derive long-horizon entropy.

With the loglinear approximation (24), the pricing kernel becomes
$$
logm_{t,t+1}=constant+[(\rho-1)\gamma(B)+(\alpha-\rho)\gamma(b_1)]v^{1/2}w_{t+1}\tag{B.ii}
$$
see [[B.ii推导|Appendix E]]. 

The key term is
$$
\gamma(b_1)=\sum^\infty_{j=0}b^j_1\gamma_j
$$
consumption growth on current utility. 

The action is in the moving average coefficients. For $j \geq 1$ we reproduce power utility: $\alpha_j = (\rho − 1)\gamma_jv^{1/2}$.
The initial term, however, is affected by $\gamma(b_1)$:
$\alpha_0 = [(\rho − 1)\gamma_0 + (\alpha − \rho)\gamma(b_1)]v^{1/2}$. 
$\alpha_0$和$\alpha_j$的推导![[a0和aj的推导|推导]]
If $\gamma(b_1) 	= \gamma_0$, we can make $\alpha_0$ large and $\alpha_j$ small for j ≥ 1, as needed, by choosing $\alpha$ and $\rho$ judiciously. 
The infinite sum is$$
\begin{aligned}
A_\infty &= \alpha(1) \\
&=[(\rho − 1)\gamma(1) + (\alpha - \rho)\gamma(b_1)]v^{1/2}\\
&=\{(\alpha − 1)\gamma(1) + (\alpha - \rho)[\gamma(b_1) - \gamma(1)]\}v^{1/2}\\
\end{aligned}$$which is close to the power utility result if $\gamma(b_1) - \gamma(1)$ is small.

With habits, we add the law of motion
$$
logh_{t+1}=logh+\eta(B)logc_t
$$
We set $\eta(1) = 1$ to guarantee that $h_t/c_t$ is stationary. 

For the ratio habit model (20), the log pricing kernel is
$$
logm_{t,t+1}=constant+[(\rho-1)-\rho\eta(B)B]\gamma(B)v^{1/2}w_{t+1}
$$
Here $\alpha_0 = (\rho − 1)\gamma_0v^{1/2}$ and $A_\infty =−\gamma(1)v^{1/2}$. 
The first is the same as power utility with curvature $1 − \rho$, the second is the same as log utility ($\rho = 0$). 
The other terms combine the dynamics of consumption growth and the habit.

For the difference habit model (21), the challenge lies in transforming the pricing kernel into something tractable. We use a loglinear approximation.

Define $z_t = log(h_t/c_t)$ so that $s_t = 1 − e^{z_t}$. If $z_t$ is stationary with mean $z = log (h/c)$, then a linear approximation of $log s_t$ around z is
$$
\begin{aligned}
logs_t &\cong constant-[(1-s)/s]z_t\\
&=constant-[(1-s)/s]log(h_t/c_t)
\end{aligned}
$$
where $s = 1 − h/c = 1 − e^z$ is the surplus ratio corresponding to z. 

The pricing kernel becomes
$$
logm_{t,t+1} = constant + (ρ − 1)(1/s)[1 − (1 − s)η(B)B]γ(B)v^{1/2}w_{t+1}.
$$
Here $\alpha_0 = (ρ − 1)(1/s)γ_0v^{1/2}$, which differs from power utility in the (1/s) term, and $A_\infty = (ρ − 1)γ(1)v^{1/2}$, which is the same as power utility.

We illustrate the properties of these models with numerical examples based on parameter values used in earlier work.We use the same consumption growth process in all four models,which helps to align their long-horizon properties.We use an ARMA(1,1) that reproduces the mean, variance, and autocorrelations of Bansal and Yaron (2004, Case I); see Appendix I. （对 [[#^5dbea3|consumption growth]] $log g_{t+1}$建ARMA(1,1)）
![[#^5dbea3]]

The moving average coefficients are $γ_0 = 1$, $γ_1 = 0.0271$, and $γ_{j+1} = \varphi_gγ_j$ for j ≥ 1 with $\varphi_g = 0.9790$. This introduces a small but highly persistent component to consumption growth.

The mean is $log g = 0.0015$, the conditional variance is $v = 0.0099^2$, and the (unconditional) variance is $0.01^2$. 

In the habit models, we use Chan and Kogan’s(2002) AR(1) habit: $η_0 = 1 − \varphi_h$ and $η_{ j+1} = \varphi_hη_j$ for j ≥ 0 and 0 ≤ $\varphi_h < 1$. We set $\varphi_h < 1$ = 0.9, which is between the Chan–Kogan choice of 0.7 and the Campbell–Cochrane (1999) choice of 0.9885. Finally, we set the mean surplus s for the difference habit model equal to one half.

![[Pasted image 20221216153140.png]]

We summarize the properties of these models in Table II (parameters and selected calculations), Figure 3 (moving average coefficients), and Figure 4 (entropy versus time horizon). In each panel of Figure 3, we compare a rep-
resentative agent model to the Vasicek model of Section I.E. We use absolute values of coefficients in the figure to focus attention on magnitudes.

![[Pasted image 20221216161058.png]]
Consider power utility with curvature $1 − α = 1 − ρ = 10$. The comparison with the Vasicek model suggests that the initial coefficient is too small (note the labels next to the bars: 0.1837 $\gg$ 0.0991) and the subsequent coefficients are too large(第一个bar相对来说低了，后面的bar相对来说高了). As a result, the model has too little one-period entropy and too much horizon dependence.

![[Pasted image 20221216161122.png]]

We see exactly that in Figure 4. The solid line at the center of the figure represents entropy for the power utility case with curvature $1 − α = 1 − ρ = 10$. One-period entropy (0.0049) is well below our estimated lower bound (0.0100), the dotted horizontal line near the middle of the figure. Entropy rises quickly as we increase the time horizon, which violates our horizon dependence bounds (plus and minus 0.0010). The bounds are represented by the two dotted lines near the bottom of the figure, centered at power utility’s one-period entropy. The model exceeds the bound almost immediately. ==The increase in entropy with time horizon is, in this case, entirely the result of the positive autocorrelation of the consumption growth process.==

The recursive utility model, in contrast, has more entropy at short horizons
and less horizon dependence. Here we set $1 − α = 10$ and $1 − ρ = 2/3$, ==the values used by Bansal and Yaron (2004)==. Recursive and power utility have similar long-horizon properties, in particular, similar values for $A_\infty = a(1)$, the infinite sum of moving average coefficients. Recursive utility takes some of this total away from later coefficients (aj for j ≥ 1) by reducing $1 − ρ$ from 10 to 2/3, and adds it to the initial coefficient $a_0$. As a result, horizon dependence at 120 months falls from 0.0119 with power utility to 0.0011. ==This is a clear improvement over power utility, but it is still slightly above our bound (0.0010)==. Further, ==$H(\infty)$ of 0.0018 hints that entropy at longer horizons is inconsistent with the tendency of long bond yields to level off or decline between 10 and 30 years==. See, for example, Alvarez and Jermann (2005,Figure 1). 

The difference habit model has greater one-period entropy than power utility (the effect of 1/s) but the same long-horizon entropy. In between, ==it has negative horizon dependence, the result of the negative autocorrelation in the pricing kernel induced by the habit==. Horizon dependence satisfies our bound at a horizon of 120 months, ==but violates it for horizons between 4 and 93 months==. Relative to power utility, this model reallocates some of the infinite sum $A_\infty$ to the initial term, but it affects subsequent terms in different ways. In our example, the early terms are negative, but later terms turn positive. The result is nonmonotonic behavior of entropy, which is mimicked, of course, by the mean yield spread.

The ratio habit model has, as we noted earlier, the same one-period entropy as power utility with $1 − ρ = 10$. Like the difference habit, it has excessive negative horizon dependence at short horizons, but, unlike that model, the
same is true at long horizons, too, as it approaches log utility ($1 − ρ = 1$). 

Overall, these models differ in both their one-period entropy and their horizon dependence. They are clearly different from each other. With the parameter values we use, some of them have too little one-period entropy and ==all of them have too much horizon dependence==. The challenge is to clear both hurdles.


