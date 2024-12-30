# Midterm

1. **$\mathbf{Beta} $ distribution** 

$$
\mathbf{Beta}(\alpha, \beta) = \int_{0}^{1} t^{\alpha-1} (1-t)^{\beta -1} dt
$$

Relation with $\mathbf{Gamma}$ distribution

$$
\mathbf{Beta}(\alpha, \beta) = \frac{\Gamma(\alpha) \Gamma(\beta)}{\Gamma(\alpha+\beta)}
$$

where $\Gamma(n) = (n-1)!, \ \Gamma(\alpha + 1) = \alpha \Gamma(\alpha) $.

If $X \sim \mathbf{Gamma}(\alpha, \beta)$, then its pdf is 

$$
f(x|\alpha, \beta) = \frac{1}{\Gamma(\alpha) \beta^{\alpha}} x^{\alpha - 1} e^{-\frac{x}{\beta}}, \quad 0 < x < \infty, \quad \alpha>0, \beta>0
$$


2. **Integration by parts**

$$
\frac{d}{dx} (u(x) v(x)) = u'(x)v(x) + u(x) v'(x)
$$

integrate on both sides

$$
\int\frac{d}{dx} (u(x) v(x))dx = \int u'(x)v(x) dx + \int u(x) v'(x) dx
$$

then 

$$
u(x)v(x) = \int u'(x)v(x) dx + \int u(x) v'(x) dx
$$  

so 

$$
\int u'(x)v(x) dx =  u(x)v(x) - \int u(x) v'(x) dx
$$

3. **pdf of normal distrubution**

$$
f(x) = \frac{1}{\sqrt{2\pi \sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}, \ -\infty < x < \infty
$$

4. **Law of Total Variance**

$$
\mathbf{Var}(W) = \mathbf{Var}(E(W|X)) + E(\mathbf{Var}(W|X))
$$


5. **Chebyshev's Inequality**

> used to describe the deviation of a random variable's distribution from its mean

For a r.v. with mean $\mu = E(x), \ \sigma^2 = \mathbf{Var}(x)$, then for each $k > 0$, we have Chebyshev's Inequality:

$$
P(|X - \mu| \geq k \sigma) \leq \frac{1}{k^2}
$$

or for any r.v. $Y$, we have

$$
P(|Y-E(Y)| \geq \epsilon) \leq (\frac{\mathbf{Var}(Y)}{\epsilon^2})
$$

Another form

$$
P(Z \geq t) \leq \frac{E(Z)}{t}
$$


6. **Delta method**

> use Taylor expansion to approximate complex non-linear method in order to transform the non-linear problem to linear problem

For a r.v. $X_n$, suppose when $n \rightarrow \infty$ its asymptotic normal distribution is normal distribution with mean $\mu$ and variance $\sigma^2$

$$
\sqrt{n}(X_n - \mu) \xrightarrow{D} N(0, \sigma^2)
$$

Then we apply a smooth function $g(x)$ to $X_n$, and use Taylor at $X_n = \mu$

$$
g(X_n) \approx g(\mu) + g'(\mu) (X_n - \mu)
$$

Then 

$$
\sqrt{n}(g(X_n) - g(\mu)) \approx g'(\mu) \cdot \sqrt{n} (X_n - \mu)
$$

Since $\sqrt{n}(X_n - \mu)$ converge on distribution $N(0,\sigma^2)$, then 

$$
\sqrt{n}(g(X_n) - g(\mu)) \xrightarrow{D} N(0, \sigma^2 [g'(\mu)]^2)
$$

7. **Taylor expansion**

$$
f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!} (x-a)^2 + \frac{f'''(a)}{3!} (x-a)^3 \cdots
$$

or in a more succinct form

$$
f(x) = \sum_{n=0}^{\infty} \frac{f^{n}(a)}{n!} (x-a)^n
$$

**Maclaurin Series** is a special case of Taylor Seires when expand at 0

$$
f(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f'''(0)}{3!} x^3 \cdots
$$

**Taylor with MGF**

$$
M_X(t) = E(e^{tX}) = \sum_{k=0}^{\infty} \frac{M_X^{ (k) }(0)}{k!} t^k
$$


8. **Minimum**

If the first derivative is zero and the second derivative is positive, then this point is a local minimum. If for all $x$, the second derivative is all positive, then this point is global minimum.


9. **Complete Sufficient Statistic**

Since the property of the exponential family, the sum of sample $T = \sum_i X_i$ is a complete statistic.

10. **Inverse function**

For function $y = g(x)$, the inverse function is $g^{-1}(y) = \log (y) $, then the pdf of $Y$ is

$$
f_Y(y) = f_X(g^{-1}(y)) \cdot | \frac{d}{dy} g^{-1}(y) |
$$

11. **MGF of normal distribution**

$$
M_X(t) = E[e^{tX}] = \int_{-\infty}^{\infty} e^{tx} f_X(x) dx
$$

the pdf of normal distribution is 

$$
f_X(x) = \frac{1}{\sqrt{2\pi}} e^{-\frac{x^2}{2}}
$$

Then the MGF is 

$$
\begin{aligned}
M_X(t) &= \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{tx - \frac{x^2}{2}} dx \\
&= e^{\frac{t^2}{2}}\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{- \frac{(x-t)^2}{2}}  dx   
\end{aligned}
$$

where the pdf of normal distribution $\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{- \frac{(x-t)^2}{2}}  dx = 1$, so 

$$
M_X(t) = e^{\frac{t^2}{2}}
$$

12. **The joint distribution of ordering statistics**

$$
f_{X_1,X_n}(x_1,x_2) = \frac{n(n-1)(x_2-x_1)^{n-2}}{\theta^n}, \quad 0 < x_1 < x_2 < \theta
$$


13. **Inequality**

**Holder inequality**

If $p,q > 1$ and $\frac{1}{p} + \frac{1}{q} =1 $, for any function $f, g$,we have 

$$
\int |f(x)g(x)| dx \leq (\int |f(x)^p dx)^{\frac{1}{p}} (\int |g(x)^q dx)^{\frac{1}{q}}
$$

If $X, Y$ are r.v., then 

$$
E[|XY|] \leq (E[|X|^p])^{\frac{1}{p}} (E[|Y|^q])^{\frac{1}{q}}
$$

where $ \frac{1}{p} + \frac{1}{p} = 1 $.

When $p=q=2$, we have **Cauchy-Schwarz Inequality**

$$
E[|XY|] \leq (E[|X|^2])^{\frac{1}{2}} (E[|Y|^2])^{\frac{1}{2}}
$$

**Minkowski's Inequality**

$$
|| X+Y ||_p \leq ||X||_p + ||Y||_p
$$

**Jensen's Inequality**

For a convex function

$$
E[g(X)] \geq g(E[X])
$$


14.  **Principle of Data Reduction**

**Sufficient Statistic** : A statistic $T(X)$ is a sufficient statistic for $\theta$ if the conditional distribution of the sample $X$ given the value of $T(X)$ does not depend on $\theta$.

**Factorization theorem** : Let $f(x|\theta)$ denote the joint pdf or pmf of a sample $X$. A statistic $T(X)$ is a sufficient statistic for $\theta$ if and only if there exist functions $g(t|\theta)$ and $h(x)$ such that, for all sample point $x$ and all parameter points $\theta$,

$$
f(x|\theta) = g(T(x)|\theta) h(x)
$$

> This theorem is most usefull in finding out sufficient statistic.

**Find sufficient statistic of exponential family** : Let $X_1, X_2, \cdots, X_n$ be i.i.d. observations from a pdf or pmf $f(x|\theta)$ that belongs to an exponential family given by

$$
f(x|\theta) = h(x)c(\theta) \exp \left( \sum_{i=1}^k w_i (\theta) t_i(x) \right)
$$

where $\theta = (\theta_1, \cdots, \theta_d), d \leq k$. Then 

$$
T(X) = \left( \sum_{j=1}^n t_1(X_j), \sum_{j=1}^n t_2(X_j), \cdots \sum_{j=1}^n t_k(X_j)\right)
$$

**Minimal Sufficient Statistics** : A sufficient statistic $T(X)$ is minimal sufficient statistic if, for any other sufficient statistic $T'(X)$, $T(X)$ is a function of $T'(X)$.

**Decision Theorem of Minimal Sufficient Statistics** : Let $f(x|\theta)$ be the pmf or pdf of a sample $X$. Suppose there exists a function $T(x)$ such that, for every two sample points $x$ and $y$, the ratio $f(x|\theta) / f(y|\theta)$ is constant as a function of $\theta$ if and only if $T(x)=T(y)$ (the konwn condition). Then $T(x)$ is a minimal sufficient statistic for $\theta$.

**Ancillary Statistics** : If the distribution of a statistic $S(\mathbf{X})$ does not depend on interested parameter, it is called an ancillary statistics.

**Complete Statistics** : Let $f(t|\theta)$ be a family of pdf or pmf for a statistic $T(X)$. The family of probability distributions is called complete if $E_{\theta} [g(T)] = 0 $ for all $\theta$ implies that $P_{\theta} (g(T)=0)=1 $ for all $\theta$. Equivalently, $T(\mathbf{X})$ is called a complete statistic.

**Basu's Theorem** : If $T(\mathbf{X})$ is a complete and (minimal) sufficient statistic, then $T(\mathbf{X})$ is independent of every ancillary statistic.

> Basu's theorem is useful in that it allows us to deduce the independence of two statistic without ever finding the joint distribution of the two statistics.

15. **The joint distribution of independent normal distribution**

For two independent r.v. $U, V$, their jonit distribution is the product of their single distribution

$$
f_{U,V}(u,v) = f_U(u) \cdot f_V(v)
$$

The pdf for each r.v. is 

$$
f_U(u) = \frac{1}{\sqrt{2\pi \sigma^2}} e^{-\frac{(u - \mu_1)^2}{2\sigma^2}}
$$

So the joint pdf is 

$$
f_{U,V}(u,v) = \frac{1}{2\pi \sigma_1 \sigma_2} \exp \left(-\frac{(u - \mu_1)^2}{2\sigma^2}-\frac{(v - \mu_2)^2}{2\sigma^2}\right)
$$

16. **Standard Cauchy Distribution**

$$
f(x) = \frac{1}{\pi (1+x^2)}, \quad -\infty < x < \infty
$$


17. **Limitation Lemma**

Let $a_1, a_2, \cdots$ be a sequence of numbers converging to $a$, that is $\lim \limits_{n \rightarrow \infty} a_n =a $,

$$
\lim\limits_{n\to\infty}\left(1+\frac{a_n}{n}\right)^n=e^a.
$$

18. **Poisson Distribution**

If $X_i \sim \mathbf{Poisson}(\lambda)$, then $E(X_i) = Var(X_i) = \lambda$


19. **Slutsky Theorem**

- Add : if $X_n, Y_n$ converge to $X, Y$, then their sum also converges to a constant

$$
X_n + Y_n \xrightarrow{p} X+Y
$$

- Multiple : if $X_n \xrightarrow{p} X$, then for constant $c$, we have $c X_n \xrightarrow{p} cX $

- if $X_n \xrightarrow{p} X, Y_n \xrightarrow{d} Y$, we have $ X_n Y_n \xrightarrow{p} X \cdot Y $













