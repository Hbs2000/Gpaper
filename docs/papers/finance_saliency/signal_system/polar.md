# Polar form



傅里叶变换有：
$$
X[k]=\sum_{n=0}^{N-1}x[n]\cdot e^{-i\cdot\frac{2\pi}N\cdot k\cdot n}
$$

由欧拉公式 $e^{-i\cdot\frac{2\pi}N\cdot k\cdot n}=\cos\left(\frac{2\pi}N\cdot k\cdot n\right)-i\sin\left(\frac{2\pi}N\cdot k\cdot n\right)$：

$$
X[k] = \sum_{n=0}^{N-1}x[n] \cos\left(\frac{2\pi}N\cdot k\cdot n\right) -i \sum_{n=0}^{N-1}x[n]\sin\left(\frac{2\pi}N\cdot k\cdot n\right)
$$

令 $a = \sum_{n=0}^{N-1}x[n] \cos\left(\frac{2\pi}N\cdot k\cdot n\right), b = - \sum_{n=0}^{N-1}x[n]\sin\left(\frac{2\pi}N\cdot k\cdot n\right)$，则 $a$ 中的每一项代表信号 $x[n]$ 在 **basis function** $\cos (\frac{2\pi}Nk)$ 上的投影，求和后表示对频率 $k$ 全部的实部贡献，$b$ 同理。因此得到如下表达：
$$
X[k]=a+bi
$$

对于虚数表达，可以得到频率 $k$ 的相位信息 $\phi = \arctan (\frac{b}{a})$ 与振幅信息 $A = \sqrt{a^2+b^2}$，根据三角函数关系 $\sin(\phi) = \sin(\arctan(\frac{b}{a}))=\frac b{\sqrt{a^2+b^2}},\cos(\phi) = \cos(\arctan(\frac{b}{a}))=\frac a{\sqrt{a^2+b^2}}$，因此有：

$$
X[k]= A (\cos\phi + i \sin\phi) = A e^{i \phi} = e^{\log (A)+i \phi}
$$

接着，做逆变换时有：
$$\begin{aligned}
x[n]&=\frac1N\sum_{k=0}^{N-1}X[k]\cdot e^{iw_kn}=\frac1N\sum_{k=0}^{N-1}A(\cos(\phi)+i\sin(\phi)) \cdot (cos(w_kn)+isin(w_kn)) \\ 
&=\frac1N\sum_{k=0}^{N-1}A\{[cos(\phi)*cos(w_kn)-sin(\phi)*sin(w_kn)]+i[cos(\phi)*sin(w_kn)+sin(\phi)*cos(w_kn)]\}
\end{aligned}$$

其中 $w_k = \frac{2 \pi k}{N}, \ k = 1 \cdots N-1$，根据辅助角公式 

$$
\begin{aligned}
    a\sin x+b\cos x &= \sqrt{a^2+b^2} \cos (x - \arctan \frac{a}{b}), b>0 \\
    a\sin x+b\cos x &= \sqrt{a^2+b^2} \sin (x + \arctan \frac{b}{a}), a>0
\end{aligned}
$$

有

$$
\begin{aligned}
    x[n] &= \frac1N\sum_{k=0}^{N-1}A\{cos(w_kn+\phi)+i*sin(w_kn+\phi)\} \\
    &= \frac1N\sum_{k=0}^{N-1}A\cdot e^{i(w_kn+\phi)}
\end{aligned}
$$












