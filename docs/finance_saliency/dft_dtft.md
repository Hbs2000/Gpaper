# DFT & DTFT


***The DFT is a special case of the sampled DTFT***

## Discrete Time Fourier Transform

对于一个连续信号 $x(t)$，进行 sample 后就得到了采样信号 $x_s(t)$：

$$
x_{s}(t)=x(t)\sum_{k=-\infty}^{\infty}\delta(t-kT)
$$

其中，$\delta$ 函数是一个周期函数，周期函数就有 Fourier Series，进一步化简得：

$$
\begin{aligned}
    x_s(t)&=x(t)\sum_{k=0}^{\infty}c_k e^{jk\omega_0 t},  \quad  c_k = \frac{1}{T}, \omega_0 = \frac{2\pi}{T} \\
    &= \frac{1}{T} \sum_{k=0}^{\infty} x(t)e^{jk\omega_0 t}
\end{aligned}
$$

  



## Discrete Fourier Transform















