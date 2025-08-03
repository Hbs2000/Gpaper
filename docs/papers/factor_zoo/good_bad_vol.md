# Good Volatility, Bad Volatility, and the Cross Section of Stock Returns

Tim Bollerslev<sup>1</sup>, Sophia Zhengzi Li<sup>2</sup>, and Bingzhi Zhao<sup>3</sup>, ***JFQA***, 2019.

1. *Duke University*
2. *Rutgers University*
3. *Bing*


Intraday data

let $p_T$ denote the **natural logrithmic price** of an arbitrary asset on day $T$. The price is assumed to follow **the generic jump diffusion**.

$$
\begin{equation}
p_T\quad=\quad\int_0^T\mu_\tau d\tau+\int_0^T\sigma_\tau dW_\tau+J_T,
\end{equation}$$

where 
- $\mu$ and $\sigma$ denote the drift and diffusive volatility processes, respectively 
- $W$ is a standard Brownian motion 
- $J$ is a pure jump process

> Jump means sudden price jumps at discrete points in time. So this equation means the price contains two parts, continous part and discrete part. 

and the unit time-interval corresponds to a trading day. We will assume that high-frequency intraday prices $p_t, p_{t+1/n}, \cdots, p_{t+1}$ are observed at $n+1$ equally spaced times over the trading day $[t,t+1]$. We will denote the natural logarithmic discrete-time return over the $i$th time-interval on day $t+1$ by $r_{t+i/n}=p_{t+i/n}-p_{t+(i-1)/n}.$

The daily realized variance (RV) is then simply defined by the summation of these within-day high-frequency squared returns

$$
\begin{equation}
\mathrm{RV}_t\quad=\quad\sum_{i=1}^nr_{t-1+i/n}^2.
\end{equation}$$

By well-known arguments, the realized variance converges (for $n \rightarrow \infty$) to the quadratic variation comprised of the separate components due to "continuous" and " jump" price increments

$$
\begin{equation}
\mathrm{RV}_t\quad\to\quad\int_{t-1}^t\sigma_s^2ds+\sum_{t-1\leq\tau\leq t}J_\tau^2,
\end{equation}
$$

thus affording increasingly more accurate ex post measures of the true latent total daily price variation for ever finer sampled intraday returns.

> $\mu$ term is negligible compared to $ds$

The realized variance measure can be differentiate between "good" and "bad",

$$
\begin{equation}
    \mathrm{RV}_t^+\quad=\quad\sum_{i=1}^nr_{t-1+i/n}^2\mathbf{1}_{\{r_{t-1+i/n>0}\}},\quad\mathrm{RV}_t^-\quad=\quad\sum_{i=1}^nr_{t-1+i/n}^2\mathbf{1}_{\{r_{t-1+i/n<0}\}}.
\end{equation}$$

The positive and negative realized semi-variance measures obviously add up to the total daily realized variation, $\mathrm{RV}_t=\mathrm{RV}_t^++\mathrm{RV}_t^-.$ Moreover, it is possible to show that

$$
\mathrm{RV}_t^+\quad\to\quad\frac{1}{2}\int_{t-1}^t\sigma_s^2ds+\sum_{t-1\leq\tau\leq t}J_\tau^2\mathbf{1}_{(J_\tau>0)}, \\ \mathrm{RV}_t^-\quad\to\quad\frac{1}{2}\int_{t-1}^t\sigma_s^2ds+\sum_{t-1\leq\tau\leq t}J_\tau^2\mathbf{1}_{(J_\tau<0)},
$$

Then the difference between the semi-variances **removes** the variation stemming from jumps. We will refer to this good minus bad realized volatility measure as the signed jump (SJ) variation

$$
\begin{equation}
\mathrm{SJ}_t\quad=\quad\mathrm{RV}_t^+-\mathrm{RV}_t^-\quad\to\quad\sum_{t-1\leq\tau\leq t}J_\tau^2\mathbf{1}_{(J_\tau>0)}-J_\tau^2\mathbf{1}_{(J_\tau<0)}.
\end{equation}
$$

The level of the volatility differs substantially across different stocks, so we scale

$$
\begin{equation}
\mathrm{RSJ}_t\quad=\quad\frac{\mathrm{SJ}_t}{\mathrm{RV}_t}.
\end{equation}$$

This normalization restricted RSJ to lie between $-1$ and $1$.

In addition to these realized variation measures based on the separately defined up and down intraday return variation, we also calculate the daily realized skewness (RSK),

$$\begin{equation}
\mathrm{RSK}_t = \frac{\sqrt{n}\sum_{i=1}^nr_{t-1+i/n}^3}{\mathrm{RV}_t^{3/2}},
\end{equation}$$

and realized kurtosis(RKT)

$$
\begin{equation}
\mathrm{RKT}_t =  \frac{n\sum_{i=1}^nr_{t-1+i/n}^4}{\mathrm{RV}_t^2},
\end{equation}
$$

In contrast to RSJ, however, which has a clear interpretation as a measure of the relative signed jump variation, RSK and RKT converge to scaled versions of the intraday jumps raised to the third and fourth power, respectively, and are not directly interpretable as standard measures of skewness and kurtosis.

Futhermore, compared to the realized variation measures, the use of higher order (greater than 2) return moments in the calculation of the realized skewness and kurtosis measures render them more **susceptible** to "large" influential observations, or outliers, and thus generally more difficult to precisely estimate.

The main cross-sectional asset pricing analyses are conducted at the **weekly** frequency. We construct the relevant weekly realized variation measures by summing the correponding daily realized variation measures over the week.

> 文章选用的窗口是五分钟。












