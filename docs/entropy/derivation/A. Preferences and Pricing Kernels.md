First class of representative agent models is based on recursive preferences or utility.

Define utility recursively with the ==time aggregator==
$$
U_t=[(1-\beta)c^\rho_t+\beta\mu_t(U_{t+1})^\rho]^{\frac{1}{\rho}}\tag{14}
$$

^ab6a3d

and ==certainty equivalent function==,
$$
\mu_t(U_{t+1})=[E_t(U^\alpha_{t+1})]^{\frac{1}{\alpha}}\tag{15}
$$

^6911a8

$U_t$ is “utility from date t on,” or continuation utility.

Additive power utility is a special case with $\alpha = \rho$. In standard terminology, $\rho < 1$ captures ==time preference== (with intertemporal elasticity of substitution(跨期替代弹性) $\frac{1}{1 -\rho}$ and $\alpha < 1$ captures ==risk aversion== (with coefficient of relative risk aversion $1 - \alpha$).
The time aggregator and certainty equivalent functions are both ==homogeneous== of degree one, which allows us to scale everything by current consumption. If we define scaled utility $u_t = \frac{U_t}{c_t}$, equation (14) becomes
$$
u_t=[(1-\beta)+\beta\mu_t(g_{t+1}u_{t+1})^\rho]^{\frac{1}{\rho}}\tag{16}
$$

^e94c19

where $g_{t+1} = \frac{c_{t+1}}{c_t}$ is consumption growth. This relation serves as a ==Bellman equation==.

With this utility function, the pricing kernel is

$$
m_{t,t+1}=\beta g^{\rho-1}_{t+1}[g_{t+1}\frac{u_{t+1}}{\mu_t(g_{t+1}u_{t+1})}]^{\alpha-\rho}\tag{17}
$$

^ec0323

注释：从utility function到$m_{t,t+1}$——[[The kreps-Porteus pricing kernel]]

By comparison, the pricing kernel with additive power utility($\alpha=\rho$) is
$$
m_{t,t+1}=\beta g^{\rho-1}_{t+1}\tag{18}
$$

^b63871

Recursive utility adds another term. It reduces to power utility in two cases:
1. when $\alpha=\rho$ 
2. when $g_{t+1}$ is iid. 

The latter illustrates the central role of dynamics.
If $g_{t+1}$ is iid, $u_{t+1}$ is constant and the pricing kernel is proportional to $g^{\alpha-1}_{t+1}$ . This is arguably different from power utility, where the exponent is $\rho - 1$,but with no 
intertemporal variation in consumption growth we cannot tell the two apart. Beyond the iid case, dynamics in consumption growth introduce an extra term to the pricing kernel—in logs, the innovation in future utility plus a risk adjustment.

Second class of models introduces dynamics to the pricing kernel directly through preferences. 
All of our habit models start with utility functions that include a ==state variable== $h_t$ that we refer to as the “habit.” 

A recursive formulation is
$$
U_t=(1-\beta)f(c_t,h_t)+\beta E_tU_{t+1}\tag{19}
$$
Typically $h_t$ is predetermined (known at $t − 1$) and tied to past consumption in some way. Approaches vary, but they all assume $\frac{h_t}{c_t}$ is stationary(==not constant==). The examples we study have “external” habits: the agent ignores any impact of her consumption choices on future values of $h_t$. They differ in the functional form of $f(c_t,h_t)$ and in the law of motion for $h_t$.

Two common functional forms are ratio and difference habits. 

With ratio habits,  $f(c_t,h_t) = \frac{(\frac{c_t}{h_t})^\rho}{\rho}$ and $\rho \leq 1$. The pricing kernel is
$$
m_{t,t+1}=\beta g^{\rho-1}_{t+1}(\frac{h_{t+1}}{h_t})^{-\rho}\tag{20}
$$
Because the habit is predetermined, it has no impact on one-period entropy. 
[[(20)推导]]

With difference habits, $f(c_t, h_t) = \frac{(c_t − h_t)^\rho}{\rho}$. The pricing kernel becomes
$$
m_{t,t+1}=\beta(\frac{c_{t+1}-h_{t+1}}{c_t-h_t})^{\rho-1}=\beta g^{\rho-1}_{t+1}(\frac{s_{t+1}}{s_t})^{\rho-1}\tag{21}
$$
where $s_t = \frac{c_t - h_t}{c_t} = 1 - \frac{h_t}{c_t}$ is the ==surplus consumption ratio==(a constant). In both cases, we gain an extra term relative to additive power utility.
推导同上，略

These models have different properties, but their long-horizon entropies are similar to some version of power utility. 

Consider models that can be expressed in the form(difference habits的推广，ratio habits 不符合)
$$
m_{t,t+1}=\beta g^\varepsilon_{t+1}\frac{d_{t+1}}{d_t}\tag{22}
$$
where $d_t$ is stationary and $\varepsilon$ is an exponent to be determined. 

##### Proposition
Then long-horizon entropy $I(\infty)$ is the same as for a power utility agent (18) with $\rho - 1 = \varepsilon$.
Elements of this proposition are reported by Bansal and Lehmann (1997)and Hansen (2012, Sections 7 and 8).

The proposition follows from the decomposition of the pricing kernel (equation (22)), the definition of the principal eigenvalue and eigenfunction (equation(10)), and the connection between the principal eigenvalue and long-horizon entropy (equation (11)). 
$$
E_t(m_{t,t+1}e_{t+1})=\lambda e_t\tag{10}
$$
$$
I(\infty)=log\lambda-Elogm_{t,t+1}\tag{11}
$$

Suppose an arbitrary pricing kernel $m_{t,t+1}$ has principal
eigenvalue $\lambda$ and associated eigenfunction $e_t$. Long-horizon entropy is $I(\infty) = log \lambda − Elogm_{t,t+1}$. Now consider a second pricing kernel $m'_{t,t+1} = m_{t,t+1}\frac{d_{t+1}}{dt}$, with $d_t$ stationary. The same eigenvalue $\lambda$ now satisfies (10) with pricing kernel $m'_{t,t+1}$ and eigenfunction $e'_t = \frac{e_t}{d_t}$.
[[Proposition推导]]
Since $d_t$ is stationary, the logs of the two pricing kernels have the same mean: $$Elog(m_{t,t+1}\frac{d_{t+1}}{dt}) = Elogm_{t,t+1}$$Thus, they have the same long-horizon entropy. Power utility is a special case with $m_{t,t+1} = \beta g^\varepsilon_{t+1}$.

We illustrate the impact of this result on our examples, which we review in reverse order. 

With difference habits, the pricing kernel (21) is already in the form of equation (22) with $\varepsilon = \rho -1$ and $d_t = s^{\rho-1}_t$. 
With ratio habits, the pricing kernel (20) does not have the right form, because $h_t$ is not stationary in a growing economy. 

An alternative is
$$
m_{t,t+1}=\beta g^{-1}_{t+1}[\frac{\frac{h_{t+1}}{c_{t+1}}}{\frac{h_t}{c_t}}]^{-\rho}
$$
which has the form of (22) with $\varepsilon =-1$ (corresponding to $\rho = 0$, log utility) and $d_t = (\frac{h_t}{c_t})^{-\rho}$. Bansal and Lehmann (1997, Section 3.4) report a similar decomposition for a model with an internal habit.

Recursive utility can be expressed in approximately the same form(21). The pricing kernel (17) can be written as
$$
m_{t,t+1}=\beta g^{\alpha-1}_{t+1}[\frac{u_{t+1}}{\mu_t(g_{t+1}u_{t+1})}]^{\alpha-\rho}
$$
 
 If $\mu_t$ is approximately proportional to $u_t$, as suggested by Hansen (2012, Section 8.2), then
$$
m_{t,t+1} \cong \beta'g^{\alpha-1}_{t+1}(\frac{u_{t+1}}{u_t})^{\alpha-\rho}
$$
where $\beta'$	 includes the constant of proportionality. The change from $\beta$ to $\beta'$ is irrelevant here, because entropy is invariant to such changes in scale. Thus, the model has (approximately) the form of (22) with $\varepsilon = \alpha - 1$ and $d_t = u^{\alpha-\rho}_t$.

All of these models are similar to some form of power utility at long horizons.We will see shortly that they can be considerably different at short horizons.