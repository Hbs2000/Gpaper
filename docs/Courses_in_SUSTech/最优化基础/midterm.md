
## 范数

### 向量范数

称一个从向量空间 $\mathbb{R}^n$ 到实数域 $\mathbb{R}$ 的**非负**函数为范数，如果它满足：

1. **正定性**：对于所有的 $v \in \mathbb{R}^n $，有 $\|v\| \geq 0$，且 $\|v\|=0$ 当且仅当 $v=0$
2. **齐次性**：对于所有的 $v \in \mathbb{R}^n $ 和 $\alpha \in \mathbb{R}$，有 $\|\alpha v\| = |\alpha| \|v\|$
3. **三角不等式**：对于所有的 $v, w \in \mathbb{R}^n $，有 $\|v+w\| \leq \|v\| + \|w\|$

最常用的向量范数为 $\ell_{p}$ 范数 ($p \geq 1$)：

$$
\|v\|_p=(|v_1|^p+|v_2|^p+\cdots+|v_n|^p)^{\frac1p};
$$

当 $p=\infty$ 时，$\ell_{\infty}$ 范数定义为

$$
\|v\|_\infty=\max_i|v_i|.
$$

对于 $\ell_{2}$ 范数，有 **Cauchy inequality**: 

$$
|a^Tb| \leq ||a||_2 ||b||_2
$$

*等号成立当且仅当 a 与 b 线性相关*．

### 矩阵范数

矩阵范数是定义在矩阵空间上的非负函数，并且满足正定性、齐次性和三角不等式．向量的 $\ell_{p}$ 范数可以比较容易地推广到矩阵的 $\ell_{p}$ 范数。当 $p=1$ 时，有：

$$
\|A\|_1=\sum_{i=1}^m\sum_{j=1}^n|a_{ij}|,
$$

即 $\|A\|_1$ 为 $A$ 中所有元素绝对值的和，当 $p=2$ 时，得到 the Forbenius norm: 

$$
\|A\|_F=\sqrt{\operatorname{Tr}(AA^{\mathrm{T}})}=\sqrt{\sum_{i,j}a_{ij}^2}.
$$

F范数具有正交不变性，即对于任何正交矩阵 $U\in\mathbb{R}^{m\times m},V\in\mathbb{R}^{n\times n} $, 我们有：

$$
\begin{aligned}
\|UAV\|_{F}^{2}& =\mathrm{Tr}(UAVV^\mathrm{T}A^\mathrm{T}U^\mathrm{T})=\mathrm{Tr}(UAA^\mathrm{T}U^\mathrm{T})  \\
&=\mathrm{Tr}(AA^\mathrm{T}U^\mathrm{T}U)=\mathrm{Tr}(AA^\mathrm{T})=\|A\|_F^2,
\end{aligned}
$$

*其中，第三个等号成立是因为 $ Tr(AB) = Tr(BA) $.*

除了从向量范数直接推广，矩阵范数还可以由向量范数诱导出来，一般称这种范数为 **算子范数** 或 **诱导范数**。给定矩阵 $A\in\mathbb{R}^{m\times n}$，以及 $m$ 维空间和 $n$ 维空间的向量范数 $\|\cdot\|_{(m)}$ 和 $\|\cdot\|_{(m)}$，其诱导的矩阵范数定义如下：

$$
\|A\|_{(m,n)}=\max_{x\in\mathbb{R}^n,\|x\|_{(n)}=1}\|Ax\|_{(m)},
$$

> [!Note]
> 
> 线性变换的角度理解该范数：矩阵 $A$ 作用于向量 $x$ ，相当于对向量 $x$ 施加了一次线性变换，线性变换之后的长度之比为 $\frac{\|Ax\|_p}{\|x\|_p}$，因此矩阵的 $\ell_{p}$ 范数是由 $A$ 产生的最大放大倍数，故称之为诱导范数 （induced form）。

在**算子范数**的定义下，矩阵的 2 范数定义如下：

$$
\|A\|_2=\max_{x\in\mathbb{R}^n,\|x\|_2=1}\|Ax\|_2.
$$

容易验证，**矩阵的 2 范数是该矩阵的最大奇异值**。


核范数：给定矩阵 $A\in \mathbb{R}^{m\times n}$, 其核范数为：

$$
\|A\|_*=\sum_{i=1}^r\sigma_i,
$$

其中 $\sigma_i,i=1,2,\cdots,r$，为 $A$ 的所有非零奇异值，$r = rank(A)$，类似于向量 l1 范数的保稀疏性。我们也经常通过限制矩阵的核范数来保证矩阵的低秩性．同时，根据范数的三角不等式（下文中的凸性），相应的优化问题可以有效求解．

### 矩阵内积

对于矩阵空间 $\mathbb{R}^{m \times n}$ 的两个矩阵 $A$ 和 $B$，除了定义他们各自的范数以外，还可以定义他们之间的内积。**范数一般用来衡量矩阵的模的大小，而内积一般用来表征两个矩阵（或其张成的空间）之间的夹角**。一种常用的内积，**Frobenius**内积定义如下：

$$
\langle A,B\rangle\overset{\mathrm{def}}{\operatorname*{=}}\mathrm{Tr}(AB^\mathrm{T})=\sum_{i=1}^m\sum_{j=1}^na_{ij}b_{ij}.
$$

## 导数

### 梯度与海瑟 (Hessian) 矩阵

**梯度**：给定函数 $f:\mathbb{R}^n\to\mathbb{R}$，且 $f$ 在点 $x$ 的一个邻域内有意义，若存在向量 $g\in\mathbb{R}^n$ 满足：

$$
\lim_{p\to0}\frac{f(x+p)-f(x)-g^\mathrm{T}p}{\|p\|}=0,
$$

其中 $\|\cdot\|$ 是任意的向量范数，就称 $f$ 在点 $x$ 处可微（或 Fréchet 可微）．此时 $g$ 称为 $f$ 在点 $x$ 处的梯度，记作 $\nabla f(x)$．如果对区域 $D$ 上的每一个点 $x$ 都有 $\nabla f(x)$ 存在，则称 $f$ 在 $D$ 上可微．

**海瑟矩阵**：如果函数 $f(x):\mathbb{R}^n\to\mathbb{R}$ 在点 $x$ 的二阶偏导数 $\frac{\partial^2f(x)}{\partial x_i\partial x_j}i,j=1,2,\cdots,n$ 都存在，则：

$$
\nabla^2f(x)=\begin{bmatrix}\frac{\partial^2f(x)}{\partial x_1^2}&\frac{\partial^2f(x)}{\partial x_1\partial x_2}&\frac{\partial^2f(x)}{\partial x_1\partial x_3}&\cdots&\frac{\partial^2f(x)}{\partial x_1\partial x_n}\\\frac{\partial^2f(x)}{\partial x_2\partial x_1}&\frac{\partial^2f(x)}{\partial x_2^2}&\frac{\partial^2f(x)}{\partial x_2\partial x_3}&\cdots&\frac{\partial^2f(x)}{\partial x_2\partial x_n}\\\vdots&\vdots&\vdots&\vdots&\vdots\\\frac{\partial^2f(x)}{\partial x_n\partial x_1}&\frac{\partial^2f(x)}{\partial x_n\partial x_2}&\frac{\partial^2f(x)}{\partial x_n\partial x_3}&\cdots&\frac{\partial^2f(x)}{\partial x_n^2}\end{bmatrix}
$$

称为 $f$ 在点 $x$ 处的海瑟矩阵。当 $\nabla^2f(x)$ 在区域 $D$ 上的每个点 $x$ 处都存在时，称 $f$ 在 $D$ 上二阶可微．若 $\nabla^2f(x)$ 在 $D$ 上还连续，则称 $f$ 在 $D$ 上二阶连续可微，可以证明此时海瑟矩阵是一个**对称矩阵**。

当 $f(x):\mathbb{R}^n\to\mathbb{R}$ 是向量值函数时，我们可以定义它的雅可比 (Jacobi) 矩阵 $J(x)\in\mathbb{R}^{m\times n}$，它的第 $i$ 行是分量 $f_i(x)$ **梯度的转置**，即

$$
J(x)=\begin{bmatrix}\frac{\partial f_1(x)}{\partial x_1}&\frac{\partial f_1(x)}{\partial x_2}&\cdots&\frac{\partial f_1(x)}{\partial x_n}\\\frac{\partial f_2(x)}{\partial x_1}&\frac{\partial f_2(x)}{\partial x_2}&\cdots&\frac{\partial f_2(x)}{\partial x_n}\\\vdots&\vdots&&\vdots\\\frac{\partial f_m(x)}{\partial x_1}&\frac{\partial f_m(x)}{\partial x_2}&\cdots&\frac{\partial f_m(x)}{\partial x_n}\end{bmatrix}.
$$

此处容易看出，**梯度 $\nabla f(x)$ 的雅可比矩阵就是 $f(x)$ 的海瑟矩阵**


## 函数

**广义实值函数**： 令 ${\overline{\mathbb{R}}}{\stackrel{\mathrm{def}}{=}}{\mathbb{R}}\cup\{\pm\infty\}$ 为广义实数空间，则映射 $f:\mathbb{R}^n\to\overline{\mathbb{R}}$ 称为广义实值函数。

广义指的就是值域多了两个特殊的值 $\pm\infty$，这里我们同样规定

$$
-\infty<a<+\infty,\quad\forall a\in\mathbb{R}
$$

以及

$$
(+\infty)+(+\infty)=+\infty,\quad+\infty+a=+\infty,\forall a\in\mathbb{R}.
$$

**适当函数**：给定广义实值函数 $f$ 和非空集合 $\mathcal{X}$．如果存在 $x\in\mathcal{X}$ 使得 $f(x)<+\infty $，并且对任意的 $x\in\mathcal{X}$，都有 $f(x)>-\infty$ 那么称函数 $f$ 关于集合 $\mathcal{X}$ 是适当的．

概括来说，适当函数 $f$ 的特点是 “*至少有一处取值不为正无穷*”，以及“*处处取值不为负无穷*”。对优化问题 $\underset{x}{\text{min}} f(x)$，**适当函数可以帮助去掉一些我们不感兴趣的函数**。

**下水平集** (sublevel set)

$\alpha$-下水平集，对于广义实值函数 $f:\mathbb{R}^n\to\overline{\mathbb{R}}$，

$$
C_\alpha=\{x\mid f(x)\leqslant\alpha\}
$$

称为 $f$ 的 $\alpha$-下水平集。

若 $C_\alpha$ 非空，我们知道 $f(x)$ 的全局极小点一定落在 $C_\alpha$ 中，因此也就无需考虑 $C_\alpha$ 之外的点。

**上方图** (epigraph)

对于广义实值函数，$f:\mathbb{R}^n\to\mathbb{\overline{\mathbb{R}}}$，

$$
\text{epi}f=\{(x,t)\in\mathbb{R}^{n+1}|f(x)\leqslant t\}
$$

上方图将**函数和集合建立了联系**，$f$ 的很多性质都可以在 $\text{epi}f$ 上得到体现．在后面的分析中将看到，我们可以通过 $\text{epi}f$ 的一些性质来反推 $f$ 的性质．

**闭函数**： 设 $f:\mathbb{R}^n\to\mathbb{\overline{\mathbb{R}}}$ 为广义实值函数，若 $\text{epi}f$ 为闭集，则称 $f$ 为闭函数。

**下半连续函数**：设广义实值函数 $f:\mathbb{R}^n\to\mathbb{\overline{\mathbb{R}}}$，若对任意的 $x\in \mathbb{R}^n$，有

$$

$$

则 $f(x)$ 为下半连续函数

虽然表面上看这两种函数的定义方式截然不同，**但闭函数和下半连续函数是等价的**，有如下定理：

**定理2.2**

设广义实值函数 $f:\mathbb{R}^n\to\mathbb{\overline{\mathbb{R}}}$，则以下命题等价：

(1) $f(x)$ 的任意 $\alpha$-下水平集都是闭集

(2) $f(x)$ 是下半连续的
 
(3) $f(x)$ 是闭函数


## 凸集

如果过集合 $C$ 中任意两点的直线都在 $C$ 内，则称 $C$ 为**仿射集**，即

$$
x_1,x_2\in C\Longrightarrow\theta x_1+(1-\theta)x_2\in C\text{,}\forall\theta\in\mathbb{R}.
$$

**线性方程组 $Ax = b$ 的解集是仿射集**．反之，任何仿射集都可以表示成一个线性方程组的解集。

如果连接集合 $C$ 中任意两点的线段都在 $C$ 内，则称 $C$ 为**凸集**，即

$$
x_1,x_2\in C\Longrightarrow\theta x_1+(1-\theta)x_2\in C\text{,}\forall0\leqslant\theta\leqslant1.
$$

**从仿射集的定义容易看出仿射集都是凸集**。

从凸集可以引出凸组合 (convex combination) 和凸包 (comvex hull) 的概念，形如

$$
\begin{aligned}x=\theta_1x_1+\theta_2x_2+\cdots+\theta_kx_k&,\\1=\theta_1+\theta_2+\cdots+\theta_k,\quad\theta_i\geqslant0,i=1,2,\cdots,k\end{aligned}
$$

的点称之为 $x_1,x_2,\cdots,x_k$ 的**凸组合**。集合 $S$ 中点所有可能的凸组合构成的集合称之为**凸包**【凸包络】，记作 $\text{conv } S$。

若在凸组合的定义中去掉 $\theta_i\geq 0$ 的限制，我们可以得到仿射包的概念．

设 $S$ 为 $\mathbb{R}^n$ 的子集，称如下集合为 $S$ 的**仿射包**：

$$
\{x\mid x=\theta_1x_1+\theta_2x_2+\cdots+\theta_kx_k,\quad x_1,x_2,\cdots,x_k\in S,\quad\theta_1+\theta_2+\cdots+\theta_k=1\},
$$

记为 $\text{affine } S$。

一般而言，**一个集合的仿射包实际上是包含该集合的最小的仿射集**。

形如 
$$
x=\theta_1x_1+\theta_2x_2,\quad\theta_1>0,\theta_2>0
$$

的点称为点 $x_1,x_2$ 的**锥组合**。若集合中任意点的锥组合都在 $S$ 中，则称 $S$ 为**凸锥**.

### 重要的凸集

**超平面和半空间**： 任取非零向量 $a$，形如 $\{x\mid a^\mathrm{T}x=b \}$ 的集合称之为超平面，形如 $\{x\mid a^\mathrm{T}x \leq b \}$ 的集合称为半空间，$a$ 是对应的超平面和半空间的法向量，一个超平面将 $\mathbb{R}^n$ 分为两个半空间．容易看出，**超平面是仿射集和凸集**，**半空间是凸集但不是仿射集**。


### 球、椭球、锥

球和椭球也是常见的凸集．球是空间中到某个点距离（或两者差的范数）小于某个常数的点的集合，并将

$$
B(x_c,r)=\{\left.x\mid\|x-x_c\|_2\leqslant r\right.\}=\{\left.x_c+ru\right|\|u\|_2\leqslant1\}
$$

称为中心为 xc，半径为 r 的 **(欧几里得) 球**．而形如
$$
\{x\mid(x-x_c)^{\mathrm{T}}P^{-1}(x-x_c)\leqslant1\}
$$
称为**椭球**。

**多面体**

我们把满足线性等式和不等式组的点的集合称为多面体，即

$$
\{x\mid Ax\leqslant b,\quad Cx=d\},
$$

其中 $A\in\mathbb{R}^{m\times n},C\in\mathbb{R}^{p\times n},x\leqslant y$，表示向量 $x$ 的每个分量均小于等于 $y$ 的对应分量，多面体是有限个半空间和超平面的交集，因此是**凸集**。

**保凸运算**

证明一个集合为凸集有两种方式．第一种是利用定义，第二种方法是说明集合 $C$ 可由简单的凸集 (超平面、半空间、范数球等) 经过保凸的运算后得到。

**定理2.3** 任意多个凸集的交集为凸集。

**定理2.4** 设 $f:\mathbb{R}^n\to\mathbb{R}^m$ 是仿射变换 ( $f(x) = Ax + b, A \in \mathbb{R}^{m \times n}, b \in \mathbb{R}^m $ )，则

(1) $S\subseteq\mathbb{R}^n$ 是凸集，$\Longrightarrow f(S)\overset{\mathrm{def}}{\operatorname*{=}}\{f(x)\mid x\in S\}$ 是凸集

(2) $C\subseteq\mathbb{R}^m$ 是凸集，$f^{-1}(\mathbb{C})\overset{\mathrm{def}}{\operatorname*{=}}\{x\in\mathbb{R}^n\mid f(x)\in\mathbb{C}\}$ 是凸集

注意到缩放、平移和投影变换都是仿射变换，因此凸集经过缩放、平移或投影的像仍是凸集．


### 分离超平面定理

本节介绍凸集的一个重要性质，即分离超平面定理和支撑超平面定理。

**分离超平面定理**：如果 $C$ 和 $D$ 是不相交的两个凸集，则存在非零向量 $a$ 和常数 $b$，使得

$$
a^\mathrm{T}x\leqslant b,\quad\forall x\in\mathbb{C},\quad\text{且 }a^\mathrm{T}x\geqslant b,\quad\forall x\in D,
$$

即超平面 $\{x\mid a^{\mathrm{T}}x=b\}$ 分离了 $C$ 和 $D$。

严格分离（即上式成立严格不等号）需要更强的假设．例如，当 C 是闭凸集，D 是单点集时，我们有如下**严格分离定理**：

$$
a^\mathrm{T}x<b,\forall x\in\mathbb{C}\text{, 且 }\quad a^\mathrm{T}x_0>b.
$$

上述严格分离定理要求点 $x_0 \notin C$，当点 $x_0$ 恰好在凸集 $C$ 上的边界时，我们可以构造**支撑超平面**：

给定集合 $C$ 及其边界上一点 $x_0$，如果 $a\neq 0$ 满足 $a^\mathrm{T}x\leqslant a^\mathrm{T}x_0,\forall x\in C$，那么称集合

$$
\{x\mid a^\mathrm{T}x=a^\mathrm{T}x_0\}
$$
为 $C$ 在边界点 $x_0$ 处的支撑超平面。

**支撑超平面定理**：如果 $C$ 时凸集，则在 $C$ 的任意边界点处都存在支撑超平面

## 凸函数

设函数 $f$ 为适当函数，如果 $\text{dom }f$ 是凸集，且
$$
f(\theta x+(1-\theta)y)\leqslant\theta f(x)+(1-\theta)f(y)
$$
对所有 $x,y\in\textbf{dom }f,0\leqslant\theta\leqslant1$ 都成立，则称 $f$ 是**凸函数**

一个函数是凸函数当且仅当**将函数限制在任意直线在定义域内的部分上时仍是凸的**，这是凸函数最基本的判定方式：

**定理2.8** $f(x)$ 是凸函数当且仅当对任意的 $x\in\mathbf{dom}f,v\in\mathbb{R}^n,g:\mathbb{R}\to \mathbb{R} $,

$$
g(t)=f(x+tv),\quad\mathbf{dom}g=\{t|x+tv\in\mathbf{dom}f\}
$$

是凸函数。

对于可微函数，除了将其限制在直线上之外，还可以利用其导数信息来判断它的凸性．具体来说，有如下的一阶条件：

**定理2.9** 对于定义在凸集上的可微函数 $f$，$f$ 是凸函数当且仅当

$$
f(y)\geqslant f(x)+\nabla f(x)^{\mathrm{T}}(y-x),\quad\forall x,y\in\mathbf{dom}f.
$$

如果函数二阶连续可微，我们可以得到下面的二阶条件：

**定理2.11** 设 $f$ 为定义在凸集上的二阶连续可微函数，则 $f$ 是凸函数当且仅当

$$
\nabla^2f(x)\succeq0,\quad\forall x\in\mathbf{dom}f.
$$

如果 $\nabla^2f(x)\succ0,\forall x\in\mathbf{dom}f$，则 $f$ 是严格凸函数

**定理2.12** 函数 f(x) 为凸函数当且仅当其上方图 $\text{epi }f$ 是凸集


### 保凸运算

目前为止，除了定义证明、一阶二阶条件、上方图，还可以通过凸函数的保凸运算得到

**定理2.13**

(1) 若 $f$ 是凸函数，则 $\alpha f$ 是凸函数，其中 $\alpha \geq 0$．

(2)若 $f_1,f_2$ 是凸函数，则 $f_1+f_2$ 是凸函数．

(3) 若 $f$ 是凸函数，则 $f(Ax + b)$ 是凸函数．

(4) 若 $f_1,f_2,\cdots,f_m$ 是凸函数，则 $f(x)=\max\{f_1(x),f_2(x),\cdots,f_m(x)\}$ 是凸函数

(5) 若对每个 $y\in\mathcal{A},\quad f(x,y)$ 关于 $x$ 是凸函数，则 $g(x)=\sup_{y\in\mathcal{A}}f(x,y)$ 是凸函数。

(6)

(7)

