The pricing kernel in a representative agent model is the marginal rate of substitution between (say) consumption at date t \[$c_t$\] and consumption in state s at t+1 \[$c_{t+1}(s)$\]. Here’s how that works with recursive preferences. With this notation, the certainty [[A. Preferences and Pricing Kernels#^6911a8|equivalent (15)]] might be expressed less compactly as
$$
\mu_t(U_{t+1})=[\sum_s\pi(s)U_{t+1}(s)^\alpha]^{\frac{1}{\alpha}}
$$
where $\pi(s)$ is the conditional probability of state s and $U_{t+1}(s)$ is continuation utility. Some derivatives of [[A. Preferences and Pricing Kernels#^ab6a3d|(14)]] and [[A. Preferences and Pricing Kernels#^6911a8|(15)]]:
$$
\frac{\partial U_t}{\partial c_t}=U^{1-\rho}_t(1-\beta)c^{\rho-1}_t
$$
$$
\frac{\partial U_t}{\partial \mu_t(U_{t+1})}=U^{1-\rho}_t\beta\mu_t(U_{t+1})^{\rho-1}
$$
$$
\frac{\partial \mu_t(U_{t+1})}{\partial U_{t+1}(s)}=\mu_t(U_{t+1})^{1-\alpha}\pi(s)U_{t+1}(s)^{\alpha-1}
$$
The marginal rate of substitution between consumption at date t and consumption in state s at t + 1 is
$$
\begin{aligned}
m_{t+1}(s)=\frac{\frac{\partial U_t}{\partial c_{t+1}(s)}}{\frac{\partial U_t}{\partial c_t}}&=\frac{[\frac{\partial U_t}{\partial \mu_t(U_{t+1})}][\frac {\partial \mu_t(U_{t+1})}{\partial U_{t+1}(s)}][\frac {\partial U_{t+1}(s)}{\partial c_{t+1}(s)}]}{\frac{\partial U_t}{\partial c_t}}\\
&=\pi(s)\beta (\frac{c_{t+1}(s)}{c_t})^{\rho-1}(\frac{U_{t+1}(s)}{\mu_t(U_{t+1})})^{\alpha-\rho}
\end{aligned}
$$
We defifine equity at t as a claim to consumption from $t + 1$ on. The return is the ratio of its value at $t + 1$, measured in units of $t + 1$ consumption, to the value at t, measured in units of t consumption.
$$
\frac{c_{t+1}}{c_t}=x_{t+1}
$$
The pricing kernel is the same with the probability $\pi(s)$ left out and the state left implicit.
$$
\begin{aligned}
m_{t+1}&=\beta (\frac{c_{t+1}}{c_t})^{\rho-1}(\frac{U_{t+1}}{\mu_t(U_{t+1})})^{\alpha-\rho}\\
&=\beta x^{\rho-1}_{t+1}[\frac{x_{t+1}u_{t+1}}{\mu_t(x_{t+1}u_{t+1})}]^{\alpha-\rho}
\end{aligned}
$$

