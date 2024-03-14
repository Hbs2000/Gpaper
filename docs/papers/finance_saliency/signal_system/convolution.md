# Convolution

对于定义在 $\mathbb{R}$ 上的周期为 2$\pi$ 的可积函数 $f,g$，定义其在 $[-\pi,\pi]$ 上的卷积（**convolution**）为

$$\begin{equation}
    (f*g)(x)=\frac1{2\pi}\int_{-\pi}^{\pi}f(y)g(x-y)dy.
\end{equation}
$$

由于其周期性，我们可以改变其中的变量顺序，得到：

$$
(f*g)(x)=\frac1{2\pi}\int_{-\pi}^{\pi}f(x-y)g(y)dy.
$$


> [!NOTE|label:Properties of Convolution]
> Linearity, commutativity, and associativity
> 1. $f*(g+h)=(f*g)+(f*h).$
> 2. $(cf)*g=c(f*g)=f*(cg)\mathrm{~for~}any\mathrm{~}c\in\mathbb{C}.$
> 3. $f*g=g*f.$
> 4. $(f*g)*h=f*(g*h).$
> 5. $f*g\textit{ is continuous}.$: $f ∗ g$ is continuous while $f$ and $g$ are merely (Riemann) integrable.
> 6. $\widehat{f*g}(n)=\hat{f}(n)\hat{g}(n).$

其中，性质6是傅里叶的独特之处：通常来说，函数相乘后的FT系数和函数做完FT后的系数再相乘的结果是不同的，然而，卷积符合这一性质，也就是说：**函数卷积后的傅里叶系数，等于函数各自 FT 系数的相乘**。也就是说，傅里叶变换将卷积转换为简单的乘法运算，此处对卷积核并没有要求，也就是说，无论使用任何卷积核，均符合这一定理。

> [!TIP|label:Proof]
$$
\begin{aligned}
\widehat{f*g}(n)& \begin{aligned}&=\frac{1}{2\pi}\int_{-\pi}^{\pi}(f*g)(x)e^{-inx}dx\end{aligned}  \\
&=\frac1{2\pi}\int_{-\pi}^{\pi}\frac1{2\pi}\left(\int_{-\pi}^{\pi}f(y)g(x-y)dy\right)e^{-inx}dx \\
&\begin{aligned}&=\frac1{2\pi}\int_{-\pi}^{\pi}f(y)e^{-iny}\left(\frac1{2\pi}\int_{-\pi}^{\pi}g(x-y)e^{-in(x-y)}dx\right)dy\end{aligned} \\
&=\frac1{2\pi}\int_{-\pi}^{\pi}f(y)e^{-iny}\left(\frac1{2\pi}\int_{-\pi}^{\pi}g(x)e^{-inx}dx\right)dy \\
&=\hat{f}(n)\hat{g}(n).
\end{aligned}
$$
> 

从概念上来说，卷积就代表着 **weighted average**。如果 $g=1$，那么二者的卷积就等于 $\frac1{2\pi}\int_{-\pi}^{\pi}f(y)dy$，相当于是 $f$ 在周期上的平均值。

**逆傅里叶变换就可理解为是一种卷积**：

$$
\begin{aligned}
S_{N}(f)(x)& =\sum_{n=-N}^N\hat{f}(n)e^{inx}  \\
&=\sum_{n=-N}^N\left(\frac1{2\pi}\int_{-\pi}^\pi f(y)e^{-iny}dy\right)e^{inx} \\
&=\frac1{2\pi}\int_{-\pi}^{\pi}f(y)\left(\sum_{n=-N}^{N}e^{in(x-y)}\right)dy \\
&=(f*D_N)(x),
\end{aligned}
$$

其中，$D_N$ is $N^{th}$ Dirichlet kernel，表达式如下：

$$
D_N(x)=\sum_{n=-N}^Ne^{inx}.
$$

**因此，理解傅里叶变换也就相当于理解 kernel**。


## A good kernel

对于 kernel 族 $\{K_n(x)\}_{n=1}^\infty $ 来说，如果满足以下条件，就称之为 **family of good kernels**：

1. 对于所有 $n\geq1$：

$$
\frac1{2\pi}\int_{-\pi}^{\pi}K_n(x)dx=1.
$$

2. 存在 $M>0$ 对于所有 $n\geq1$：

$$
\int_{-\pi}^{\pi}\left|K_n(x)\right|dx\leq M.
$$

3. 对于每一个 $\delta >0$，

$$
\int_{\delta\leq|x|\leq\pi}\left|K_n(x)\right|dx\to0,\quad\mathrm{~as~}n\to\infty.
$$




The convolution itself is also a function fo $x$, denoted as $h(x)$

通过卷积，能够使函数变得更加 smooth：

<div align = 'center'>

![](/docs/finance_saliency/image/20231215PP1.png)
</div>


卷积符合结合律和交换律：

$$
\begin{aligned}
    f*(g*h)&=(f*g)*h \\
    f*(g+h)&=f*g+f*h.
\end{aligned}
$$

式 $\ref{1}$ 有一种非常直觉的理解，如果我们认为 $f(u)$ 是固定的，那么 $g(x-u)$ 就相当于是将原本的 $g(u)$ 沿着横轴反过来，并且沿着 $x$ 不断 moving，二者最终结合的结果也就是**卷积的过程**。

<div align='center'>

![](image/20231216PP1.png)
</div>

在逐渐深入 Parseval 定理的过程中，中间又涉及到了 Wiener-Khinchin theorem，搞得晕头转向，在网上搜寻了大量资料，但是并不能解释我的疑惑，同时，我逐渐感觉到目前对于傅里叶的基础概念都不是十分了解，这样下去项目前景恐怕不甚明朗，这样不行，因此挑选了一本 textbook，对于所需部分逐字精读，疑惑慢慢解开，逐渐也有一些灵感了。










