# Parseval's theorem

## Proof 

对于一连续时域函数 $f(t)$，其傅里叶变换与逆傅里叶变换为：

$$
F(\omega)=\int_{-\infty}^{\infty}f(t)e^{-j\omega t}dt, \quad f(t)=\frac1{2\pi}\int_{-\infty}^{\infty}F(\omega)e^{j\omega t}d\omega 
$$

Parseval's theorem 证明时域能量等于频域能量，即为：

$$
\int_{-\infty}^{\infty}|f(t)|^2dt=\frac1{2\pi}\int_{-\infty}^{\infty}|F(\omega)|^2d\omega  
$$

> [!TIP|label: Complex conjugate]
> 通过 magnitude 的平方来衡量频域上的能量，而复数的 magnitude 的平方，等于其与其共轭复数的乘积。
> 
> 对于复数 $z = a+bi$ 来说，$a$ 和 $b$ 是实数，而 $i$ 是虚数单位，有 $i^2 = -1$，其共轭复数为 $z^* = a - bi$。
>
> 二者 magnitude 相等 $|z| = |z^*| =\sqrt{a^2+b^2}$，并且 $z\cdot z^*=(a+bi)(a-bi)=a^2+b^2$
>
> 对于函数 $f(t)$ 的共轭 $f(t)^*$ 来说，其傅里叶变换为：
$$
F^*(\omega)=\int_{-\infty}^\infty f^*(t)e^{-j\omega t}dt
$$
> 根据 $(ab)^* = a^* b^*$ 以及 $e^{-j\omega t}=(e^{j\omega t})^*$，有
$$
F^*(\omega)=\left[\int_{-\infty}^\infty f(t)e^{j\omega t}dt\right]^*
$$
> 

$$
\begin{aligned}
    \int_{-\infty}^{\infty}|f(t)|^2dt &= \int_{-\infty}^{\infty} f(t)f^*(t) dt \\
    &= \int_{-\infty}^{\infty} \left[ \frac1{2\pi}\int_{-\infty}^{\infty}F(\omega)e^{j\omega t}d\omega   \right] f^*(t) dt \\
    &= \frac1{2\pi} \int_{-\infty}^{\infty} F(\omega) \left[ \int_{-\infty}^{\infty} f^*(t)  e^{j\omega t} dt \right]d\omega \\
    &= \frac1{2\pi} \int_{-\infty}^{\infty} F(\omega) \left[ \int_{-\infty}^{\infty} f(t)  e^{j(-\omega) t} dt \right]^* d\omega \\
    &= \frac1{2\pi} \int_{-\infty}^{\infty} F(\omega) F(\omega)^* d\omega =  \frac1{2\pi}\int_{-\infty}^{\infty}|F(\omega)|^2d\omega  
\end{aligned}
$$

## Relation to Neuhierl and Varneskov (2021)



在 Neuhierl and Varneskov (2021) 中，协方差进行傅里叶分解得到 cospectral density：

$$
C_{yx}(h)=\mathrm{Cov}(\mathbf{y}_t,\mathbf{x}_{t-h}),\quad f_{yx}(\lambda)=\frac1{2\pi}\sum_{h=-\infty}^\infty\mathbf{C}_{yx}(h)e^{-\mathrm{i}\lambda h},
$$



通过 Parseval's theorem 自然应该得到的是：

$$
\int_{-\infty}^{\infty}|C_{yx}(h)|^2dh=\frac1{2\pi}\int_{-\infty}^{\infty}|f_{yx}(\lambda)|^2d\lambda
$$

这反映出时域信息（协方差）与频域信息（cospectral density）的等价性。然而，实际上文章给出的却是：

$$
C_{yx}(0)=2\pi\int_0^\infty f_{yx}(\lambda)d\lambda
$$

这一切还要从 **Wiener-Khinchin theorem** 说起。

### Wiener-Khinchin theorem

对于一个信号 $x(t)$ 来说，其 autocorrelation function $R_{xx}(\tau)$ 以及 power spectral density $S_{xx}(\omega)$ 如下：

$$
\begin{aligned}
S_{xx}(\omega)&=\frac1{2\pi}\int_{-\infty}^\infty R_{xx}(\tau)e^{-j\omega\tau}d\tau \\
R_{xx}(\tau)&=\int_{-\infty}^\infty S_{xx}(\omega)e^{j\omega\tau}d\omega\end{aligned}
$$

将 $R_{xx}(\tau)$ 替换为两个信号 $y_t, x_{t-h}$ 之间的 cross-covariance $C_{yx}(h)$ 时，相应的 $f_{yx}(\lambda)$ 也就充当了 $C_{yx}(h)$ 的 power spectral density，因此有：

$$
\begin{aligned}
&C_{yx}(h)=\int_{-\infty}^{\infty}f_{yx}(\lambda)e^{j\lambda h}d\lambda  \\
&f_{yx}(\lambda)=\frac{1}{2\pi}\int_{-\infty}^{\infty}C_{yx}(h)e^{-j\lambda h}dh
\end{aligned}
$$

> [!NOTE|label: Power spectral density]
> The PSD show us how the power of a signal is distributed across different frequencies. PSD is essentially the Fourier Transform of the autocorrelation function


当 lag $h$ 为 0 时，有：

$$
C_{yx}(0)=\int_{-\infty}^{\infty}f_{yx}(\lambda)e^{j\lambda\cdot0}d\lambda  = \int_{-\infty}^{\infty}f_{yx}(\lambda)d\lambda
$$

对于实值信号（real-valued signal）来说，$f_{yx}$ 关于频率轴（frequency axis）对称，因此有

$$
C_{yx}(0)=2\int_{0}^{\infty}f_{yx}(\lambda)d\lambda
$$

等式两侧同乘 $\pi$，可得【没懂】：

$C_{yx}(0)=2\pi\int_0^\infty f_{yx}(\lambda)d\lambda\simeq\frac{2\pi}{T-1}\sum_{j=1}^{T-1}\Re{\left(f_{yx}(\lambda_j)\right)}, f_{yx}(\lambda)=\frac1{2\pi}\sum_{h=-\infty}^\infty\mathbf{C}_{yx}(h)e^{-\mathrm{i}\lambda h}$

$$
C_{yx}(0)=2\pi\int_0^\infty f_{yx}(\lambda)d\lambda
$$

> [!NOTE|label:Relationship bewteen two theorems]
> Both theorems deal with the relationship between time domain and frequency domain representations of a signal or a process. 
> 
> While *Parseval's theorem is broader and applies to any signal*, the Wiener-Khinchin theorem is specific to autocorrelation functions and power spectral densities.
>
>  In the context of cross-covariance $C_{yx}$ and cospectral density $f_{yx}$, these theorems intersect

## The importance of real part

明天再做
