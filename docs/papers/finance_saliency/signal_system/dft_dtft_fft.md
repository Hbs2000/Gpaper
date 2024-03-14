# DFT, DTFT and FFT

***The DFT is a special case of the sampled DTFT***

DTFT 对离散信号进行傅里叶变换，得到的频谱是连续的

$$
X_{s}(\omega)=\sum_{k=-\infty}^{\infty}  x[k] e^{-jk\omega T}
$$

这一点非常不利于后续的计算和处理。

进而采用 DFT，在 DTFT 连续频谱的基础上进行离散化采样，实现了用离散表示离散。

$$
X(\omega)= \sum_{k=0}^{N-1} x[k] e^{-jkn \frac{2\pi}{N}}
$$


总结来说就是：

$$
\begin{aligned}
    \text{Discrete} & \xRightarrow{DTFT} \text{Continuous} \\
    \text{Discrete} & \xRightarrow{DFT} \text{Discrete}
\end{aligned}
$$

## Discrete Time Fourier Transform

对于一个连续信号 $x(t)$，进行 sample 后就得到了采样信号 $x_s(t)$：

$$
x_{s}(t)=x(t)\sum_{k=-\infty}^{\infty}\delta(t-kT)
$$

其中，$\delta(t-kT)$ 函数是一个周期函数，周期函数就有 Fourier Series，进一步化简得：

> [!NOTE|label:单位脉冲函数]
$$
\left.\delta[n]=\left\{\begin{array}{ll}0,&n\neq0\\1,&n=0\end{array}\right.\right.
$$
>

$$
\begin{aligned}
    x_s(t)&=x(t)\sum_{k=-\infty}^{\infty}c_k e^{jk\omega_0 t},  \quad  c_k = \frac{1}{T}, \omega_0 = \frac{2\pi}{T} \\
    &= \frac{1}{T} \sum_{k=-\infty}^{\infty} x(t)e^{jk\omega_0 t}
\end{aligned}
$$

两边同取傅里叶变换：

$$
\begin{equation}
    X_{s}(\omega)=\frac{1}{T}\sum_{k=-\infty}^{\infty}X(\omega-k\omega_{0})
\end{equation}
$$

其中 $x(t)$ 由于乘上了 $e^{jk\omega_0 t}$ 从而发生频谱位移。

此时我们发现，尽管采样出的 $x_s(t)$ 是离散的，但所得到的傅里叶变换得到的 $X_s(w)$ 确实是 continuous。

上述变换是 modulation 的视角，将采样信号频谱分解为不同频率，可以很容易得出在满足 Nyquist 采样定理的情况下可以恢复出原有连续信号。

另一种变换如下

$$
x_{s}(t)=\sum_{k=-\infty}^{\infty}x(t)\delta(t-kT)=\sum_{k=-\infty}^{\infty}x(kT)\delta(t-kT)
$$

> 区别就在于，第一种是先用傅里叶级数表示周期函数 $\delta$，在进行傅里叶变换。
> 
> 第二种是先利用脉冲函数性质，再进行傅里叶变换。

如果我们 denote $x[k] = x(kT)$，那么有：

> 尽管 $x[k]$ 写成与 $T$ 无关的形式，但是实际上每个 $x[k]$ 都与 $T$ 有关，它们相邻之间的差就是 sampling time $T$

$$
x_{s}(t)=\sum_{k=-\infty}^{\infty}x[k]\delta(t-kT)
$$

进行傅里叶变换：

$$
\begin{equation}
    X_{s}(\omega)=\sum_{k=-\infty}^{\infty}  x[k] e^{-jk\omega T}
\end{equation}
$$

对比两种方式，方式一将原有信号的频谱分隔开，是调制信号的视角。而方式二可以将信号一个一个区分开，对于不同 $k$，exp 的取值是不一样的。

因为两种方式本质都是一样的，所以此时 $X_s (w)$ 仍然是连续的，对于计算机来说，只能处理离散值，所以连续的频谱并不是我们想要的。

对于式（2）我们进一步深入，let $ \Omega = \omega T$，

$$
X_{s}(\frac{\Omega}{T})=\sum_{k=-\infty}^{\infty}x[k]e^{-jk \Omega}
$$

此时等式右侧已经与 $T$ 无关，但左侧仍有 $T$，继续定义 $X(\Omega) = X_s(\frac{\Omega}{T})$，有：

$$
X(\Omega) = \sum_{k=-\infty}^{\infty}x[k]e^{-jk\Omega}
$$

这就是 **discrete-time Fourier transform** of $x[k]$，表示为：

$$
\begin{aligned}
    \mathcal{F}_{DT}\{x[k]\} &= X(\Omega) = \sum_{k=-\infty}^{\infty}x[k]e^{-jk\Omega} \\
    \text{or } &= \sum_{k=0}^{\infty}x[k]e^{-jk\Omega} \quad \text{ for } k<0, x[k]=0
\end{aligned}
$$

> [!NOTE|label:connection with z transform]
> DTFT is a special case of z-transform when $z = e^{j \Omega}$
$$
X\left(z\right)=\sum_{k=0}^{N}x\left[k\right]z^{-k} |_{z=e^{j \Omega}} =X\left(\Omega\right)
$$
>
> Just like Fourier Transform is a special case of Laplaze transform

### Inverse-DTFT

$$
\begin{aligned}
    &\int_{\Omega_{1}}^{\Omega_{1}+2\pi}X\left(\Omega \right)e^{j n \Omega}d\Omega \\
    =& \int_{\Omega_{1}}^{\Omega_{1}+2\pi} \sum_{k=-\infty}^{\infty}x[k] e^{-j k \Omega} e^{j n \Omega} d\Omega  \\
    =& \sum_{k=-\infty}^{\infty}x(k)\int_{\Omega_{1}}^{\Omega_{1}+2\pi}e^{-j(k-n)\Omega}d\Omega  \\
    =& 2\pi x[n] 
\end{aligned}
$$

因此有：

$$
x[n] = \frac{1}{2\pi} \int_{\Omega_{1}}^{\Omega_{1}+2\pi}X\left(\Omega \right)e^{j n \Omega}d\Omega
$$

### Properites

(1) **Periodicity**

$$
X(\Omega + 2 \pi ) = \sum_{k=0}^{\infty}x[k]e^{-jk (\Omega+2\pi)}  = \sum_{k=0}^{\infty}x[k]e^{-jk\Omega} = X(\Omega)
$$
 

(2) **Linearity**

$$
\mathcal{F}_{DT}\left\{a \cdot x[k]+b \cdot x[k] \right\}=a \mathcal{F}_{DT} \left\{x[k]\right\}+b\mathcal{F}_{DT}\left\{x[k]\right\}.
$$

(3) **Time-shifting**

$$
\begin{aligned}
    \mathcal{F}_{DT} \{ x[k-m] \} &= \sum_{k=0}^{\infty}x[k-m]e^{-jk\Omega} \\
    &= \sum_{p=-m}^{\infty}x[p]e^{-jp\Omega}  e^{-jm\Omega}  \quad (p=k-m,m>0) \\
    &= \sum_{p=0}^{\infty}x[p]e^{-jp\Omega} e^{-jm\Omega}  \\
    &= X(\Omega) e^{-jm\Omega}
\end{aligned}
$$

(4) **Modulation**

$$
\begin{aligned}
    \mathcal{F}_{DT} \left\{ x[k] e^{jk \Omega_0} \right\} &= \sum_{k=0}^{\infty} e^{jk\Omega_0} x[k]e^{-jk\Omega} \\
    &= \sum_{k=0}^{\infty} x[k] e^{-jk(\Omega-\Omega_0)} \\
    &= X(\Omega-\Omega_0)
\end{aligned}
$$


一个信号乘上 $\cos \Omega_0 $ 相当于：

$$
\cos \Omega_0 \Rightarrow \frac{1}{2} (e^{j\Omega_0}+e^{-j\Omega_0})
$$

造成的效果是 phase 的平移，变为一半后分散到两边去。因此又称为 $\cos \Omega_0$ carrier，意为载着原来的信号跑。

$x[k] e^{jk \Omega_0}$ 相当于 $x[k]$ 乘上一个 $\cos$ 或 $\sin$，使 phase 进行平移。


(5) **Real** $x[k]$

$$
\begin{aligned}
    X(\Omega)&=\sum_{k=0}^{\infty}x[k]e^{-jk\Omega}  \\
    &= \underbrace{\sum_{k=0}^{\infty}x[k] \cos k\Omega}_{\text{even}} +  j \underbrace{\sum_{k=0}^{\infty}x[k] \sin k\Omega}_{\text{odd}}
\end{aligned}
$$

(6) **Convolution in time**

$$
x[k]*y[k]\xrightarrow{DTFT}X(\Omega) Y(\Omega)
$$

(7) **Convolution in frequency**

$$
\mathcal{F}_{DT} \{x[k]y[k] \}   X(\Omega) * Y(\Omega)
$$

(8) **Parseval's Theorem**

$$
\sum_{k=0}^{\infty} x^2[k] = \frac{1}{2\pi} \int_{2\pi} = |X(\Omega)|^2 d \Omega
$$



### Connection to DFT

我们希望找到一个工具，不再是 $\text{Discrete} \xrightarrow{DTFT} \text{Continuous}$，而是 $\text{Discrete} \xrightarrow{DFT} \text{Discrete}$。接下来举例说明。

**DTFT for periodic functions.**

Consider a periodic function $x[k]$ with period $N$，取其中 $N$ 个点，得到 $x_0[k]$：

$$
x_0[k]=\begin{cases}
x[k], \quad  & 0 \leq k \leq N-1 \\
0 \quad & \text{elsewhere}
\end{cases}
$$

$x[k]$ 可被看作是 $x_0[k]$ 与 $\delta[k-nN]$ 的卷积

$$
x[k]=x_{0}[k]*\sum_{n=-\infty}^{\infty}\delta[k-nN]
$$

对其做 DTFT：

$$
\mathcal{F}_{DT} \{ x_0[k] \} = X_0 (\Omega) = \sum_{k=0}^{N-1} x[k] e^{-jk\Omega}
$$

对两侧做 DTFT，有：

$$
\begin{aligned}
    X(\Omega)&=X_{0}(\Omega)\sum_{n=-\infty}^{\infty}\mathcal{F}_{DT}\left\{\delta\left[k-nN\right]\right\} \\
    &= X_{0}(\Omega)\sum_{n=-\infty}^{\infty}\sum_{k=-\infty}^{\infty} \delta [k-nN] e^{-jk \Omega} \\
    &= X_{0}(\Omega)\sum_{n=0}^{\infty}e^{-jnN\Omega}
\end{aligned}
$$

因为

$$
\begin{aligned}
    \delta_T(t) &= \sum_{k=-\infty}^{\infty} \delta(t-kT) = \sum_{k=-\infty}^{\infty} \frac{1}{T} e^{jk \frac{2\pi}{T}t} \\
    &= \sum_{n=-\infty}^{\infty} \frac{1}{T} e^{-jn \frac{2\pi}{T}t} \\
\Longrightarrow & \frac{1}{T}\sum_{n=-\infty}^{\infty}e^{-jn\frac{2\pi}{T}t}=\sum_{n=-\infty}^{\infty}\delta\left(t-nT\right)
\end{aligned}
$$

令 $t = \Omega, T = \frac{2\pi}{N}$，有：

$$
\frac{N}{2\pi}\sum_{n=-n}^{\infty}e^{-jnN\Omega}=\sum_{n=-\infty}^{\infty}\delta\left(\Omega-n\frac{2\pi}{N}\right)
$$

因此带入有：

$$
\begin{aligned}
    X(\Omega)&=X_{0}(\Omega) \frac{2\pi}{N} \sum_{n=-\infty}^{\infty}\delta\left(\Omega-n\frac{2\pi}{N}\right) \\
    &= \frac{2\pi}{N}\sum_{n=-\infty}^{\infty}X_0\left(n\frac{2\pi}{N}\right)\delta\left(\Omega-n\frac{2\pi}{N}\right) \\
\end{aligned}
$$

因此取 Inverse 有：

$$
\begin{aligned}
    \mathcal{F}^{-1}_{DT} \{ X(\Omega) \} &= \frac{1}{2\pi} \int_0^{2\pi}   X(\Omega) e^{jk \Omega} d\Omega \\
    &=  \frac{1}{N} \sum_{n=-\infty}^{\infty}X_0\left(n\frac{2\pi}{N}\right) \int_0^{2\pi} \delta\left(\Omega-n\frac{2\pi}{N}\right) e^{jk \Omega} d \Omega \\
    &= \frac{1}{N} \sum_{n=-\infty}^{\infty}X_0\left(n\frac{2\pi}{N}\right) e^{jkn\frac{2\pi}{N}}
\end{aligned}
$$

其中

$$
\begin{aligned}
    X_{0}\left(n\frac{2\pi}{N}\right)&=\sum_{k=0}^{N-1}x [k]e^{-jkn\frac{2\pi}{N}} \\
    x[k] &= \frac{1}{N} \sum_{n=0}^{N} X_{0}\left(n\frac{2\pi}{N-1}\right) e^{jkn\frac{2\pi}{N}}
\end{aligned}
$$


$\mathcal{F}^{-1}_{DT} \{ X(\Omega) \}$ 就是 $x[k]$，也就是将 $x[k]$ 做了完全离散的表达。这告诉我们，**如果是周期信号，通过 DTFT 可以实现用离散表达离散**。


## Discrete Fourier Transform

仅在周期函数中通过 DTFT 实现离散表达还是太麻烦了，我们希望找到一种更加方便的方式，也就是 DFT。

对于一个信号 $x[k]$ 只取其中的 $N$ 个点

$$
x_N[k] = \begin{cases}
    x[k] \quad & 0 \leq k \leq N-1 \\
    0 \quad & \text{elsewhere}
\end{cases}
$$

那么对 $x_N[k]$ 取 **DTFT**，有

$$
\begin{aligned}
    X_{N}(\Omega)&=\sum_{k=-\infty}^{\infty}x_{N}\left[k\right]e^{-jk\Omega} \\
    &= \sum_{k=0}^{N-1}x[k]e^{-jk\Omega}
\end{aligned}
$$

我们希望 $X_{N}(\Omega) \approx X(\Omega) $，但此时仍然是**连续**的，通过 N-point discretized frequency resp，对频谱进行**离散化采样**：

> 也就是说，DFT 是在 DTFT 的基础上进行频谱离散化

$$
\begin{aligned}
    X_{s}(\Omega)&=X_{N}(\Omega)\sum_{n=0}^{N-1}\delta(\Omega-n\frac{2\pi}{N}) \\
    &= \sum_{n=0}^{N-1} X_{N}(n\frac{2\pi}{N})\delta(\Omega-n\frac{2\pi}{N})
\end{aligned}
$$

Define $X[n] = X_N (n\frac{2\pi}{N}) $，带入则有

$$
X[n]=X_{N}\left(n\frac{2\pi}{N}\right)=\sum_{k=0}^{N-1}x[k]e^{-jkn\frac{2\pi}{N}}.
$$

就得到了 $x[n]$ 的 **Discrete Fourier Transform** 表达：

$$
\mathcal{F}_D \{ x[k] \} = \sum_{k=0}^{N-1} x[k] e^{-jkn \frac{2\pi}{N}}
$$

### Inverse-DFT

离散化后，怎么样才算拟合的好，就看逆变换能不能换回来，逆变换结果如下：

$$
\begin{aligned}
    &\sum_{n=0}^{N-1} X[n] e^{jkn \frac{2\pi}{N}} \\
    = & \sum_{n=0}^{N-1}\left(\sum_{m=0}^{N-1}x[m]e^{-jmn\frac{2\pi}{N}}\right)e^{jkn\frac{2\pi}{N}} \\
    = & \sum_{m=0}^{N-1}x[m] \left(\sum_{n=0}^{N-1}e^{-jmn\frac{2\pi}{N}}e^{jkn\frac{2\pi}{N}}\right) \\
    = & \sum_{m=0}^{N-1}x[m] \sum_{n=0}^{N-1}e^{j(k-m)n\frac{2\pi}{N}}
\end{aligned}
$$

接下来，要具体分析后一项，当 $m=0$ 时，有

$$
\sum_{n=0}^{N-1}e^{jkn\frac{2\pi}{N}} = 1 + e^{jk1\frac{2\pi}{N}}+e^{jk2\frac{2\pi}{N}}+\cdots + e^{jk (N-1) \frac{2\pi}{N}}
$$

对于其中每一项形如 $e^{jk1\frac{2\pi}{N}}$，称之为 rotator，任何东西乘上该项，**在复数平面中都会旋转一个角度**。

假设 $k=2,N=5$，则 $ e^{jk\frac{2\pi}{N}} = e^{j \frac{4\pi}{5}} $，那么对于 $n$ 从 $0$ 到 $N-1$ 的累加过程中，取值为：

$$
1, e^{j \frac{4\pi}{5}} ,e^{j \frac{8\pi}{5}} ,e^{j \frac{12\pi}{5}},e^{j \frac{16\pi}{5}}
$$

体现在横坐标为实数，纵坐标为虚数的附属空间内，就是**将 $2\pi$ 的圆五等分**，**因此该五个向量相加为零**。

接着，还有一种例外情况，就是当 $k=m$ 时，此时累加和为 $1$，因此，有

$$
\sum_{n=0}^{N-1}e^{j(k-m)n\frac{2\pi}{N}} = 
\begin{cases}
    0 \quad m \neq k \\
    N \quad m=k
\end{cases}
$$

因而可以将原式化为：

$$
\begin{aligned}
    &\sum_{m=0}^{N-1}x[m] \sum_{n=0}^{N-1}e^{j(k-m)n\frac{2\pi}{N}} = x[k]\cdot N \\
    \Longrightarrow & x[k]= \frac{1}{N} \sum_{k=0}^{N-1} X[n] e^{jkn\frac{2\pi}{N}}.
\end{aligned}
$$

就得到了该离散频谱的逆傅里叶变换，我们发现该结果足以将 $x[t]$ 复原出来。

> [!NOTE|label:N]
> 在 time domain 和 frequency domain 的取值数目要保证一样，使其有一定的联系。
>
> 并且，根据上述分析，如果取 $N+1$ 结果都会比较麻烦，因为在复数平面里不一定能够完全抵消。

接下来，$N$ 取值的大小也会带来麻烦，如果 $N$ 非常的大，计算起来十分不方便。$N$ 的数目，在傅里叶变换时，就是乘法的次数，总共有 $N$ 个频率，因此时间复杂度就是 $N^2$。乘法和加法中，乘法的计算 cost 更大。因此，后续引入了 FFT，用于加速傅里叶变换的速度。

## FFT

对 $N$ 的适当选取，能够大大简化计算时长。






