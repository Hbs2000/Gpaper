# Noisy Input and Gradient 

## Math formula of Loss function with noisy input

考虑损失函数 $\mathcal{L}(x)$ 在 $x_0$ 处的泰勒展开

$$
\mathcal{L}(\mathbf{x})\approx\mathcal{L}(\mathbf{x}_0)+\nabla\mathcal{L}^T(\mathbf{x}-\mathbf{x}_0)+\frac{1}{2}(\mathbf{x}-\mathbf{x}_0)^T\mathbf{H}(\mathbf{x}-\mathbf{x}_0)
$$

> 第二项为梯度项，第三项是 Hessian 项，其中 Hessian 矩阵是函数的二阶导数方阵
$$
\begin{gathered}\mathbf{H_x}\mathcal{L}=\begin{bmatrix}\frac{\partial^2\mathcal{L}}{\partial x_1^2}&\frac{\partial^2\mathcal{L}}{\partial x_1\partial x_2}&\cdots&\frac{\partial^2\mathcal{L}}{\partial x_1\partial x_n}\\\frac{\partial^2\mathcal{L}}{\partial x_2\partial x_1}&\frac{\partial^2\mathcal{L}}{\partial x_2^2}&\cdots&\frac{\partial^2\mathcal{L}}{\partial x_2\partial x_n}\\\vdots&\vdots&\ddots&\vdots\\\frac{\partial^2\mathcal{L}}{\partial x_n\partial x_1}&\frac{\partial^2\mathcal{L}}{\partial x_n\partial x_2}&\cdots&\frac{\partial^2\mathcal{L}}{\partial x_n^2}\end{bmatrix}\end{gathered}
$$
> 对于损失函数来说, $\frac{\partial^2 \mathcal{L}}{\partial x_i^2}$ 表示在其他输入不变时, $x_i$ 微小改变导致的斜率变化. $\frac{\partial^2\mathcal{L}}{\partial x_i\partial x_j}$ 表示 $x_i$ 和 $x_j$ 联合变化时的交叉影响.
 
在输入加噪场景中，我们需要带入 $x = x_0+\varepsilon$

$$
\mathcal{L}(\mathbf{x}_0+\varepsilon)=\mathcal{L}(\mathbf{x}_0)+\nabla_\mathbf{x}\mathcal{L}^T\varepsilon+\frac{1}{2}\varepsilon^T\mathbf{H}_\mathbf{x}\mathcal{L}\varepsilon+\mathcal{O}(\|\varepsilon\|^3)
$$

因为加入噪音为 $\varepsilon \sim \mathcal{N}(0,\sigma^2 \mathbf{I})$, 所以其

- 噪声均值为零 $\mathbb{E}[\varepsilon]=0$
- 协方差为对角矩阵 $\mathrm{Cov}(\varepsilon_i,\varepsilon_j)=\begin{cases}\sigma^2&i=j\\0&i\neq j&\end{cases}$

关于泰勒展开的期望推导

1. 常数项 $\mathbb{E}[\mathcal{L}(\mathbf{x}_0)]=\mathcal{L}(\mathbf{x}_0)$
2. 一阶项 $\mathbb{E}[\nabla_\mathbf{x}\mathcal{L}^T\varepsilon]=\nabla_\mathbf{x}\mathcal{L}^T\underbrace{\mathbb{E}[\varepsilon]}_0=0$
3. 二阶项

$$
\mathbb{E}\left[\varepsilon^T\mathbf{H}\varepsilon\right]=\mathrm{tr}\left(\mathbf{H}\mathrm{Cov}(\varepsilon)\right)=\mathrm{tr}\left(\mathbf{H}\cdot\sigma^2\mathbf{I}\right)=\sigma^2\mathrm{tr}(\mathbf{H})
$$

所以取关于噪声取均值得到 

$$
\mathbb{E}_\varepsilon[\mathcal{L}(\mathbf{x}_0+\varepsilon)]=\mathcal{L}(\mathbf{x}_0)+\frac{\sigma^2}{2}\mathrm{tr}(\mathbf{H}_\mathbf{x}\mathcal{L})
$$

也就是说相当于在原本的损失函数基础上惩罚了 Hessian 矩阵的迹. 它衡量了周围所有微小球形方向上损失函数的平均弯曲程度. 使得模型在输入点 $x$ 周围一个**微小邻域**内损失函数变化得尽可能平缓, 对于输入的小扰动 $\epsilon$ **变得不敏感**.

> Hessian 矩阵($\mathbf{H}$)特征值 $\lambda_i$ 描述函数在不同方向的曲率，$\lambda_i > 0$ 则是下凸，$\lambda_i < 0 $ 为上凸，$\lambda_i = 0$ 为平坦。

迹的物理意义就是

$$
\mathrm{tr}(\mathbf{H})=\sum_{i=1}^d\lambda_i=\text{平均曲率}\times d
$$

这里噪声代表的平滑性要求也就是最小化 $\mathrm{tr}(\mathbf{H})$ 等价于

- **抑制高曲率方向**（避免陡峭变化）
- **促进平坦区域**（输出对输入不敏感）


## Equivalent form

上文提到, 加噪通过选择令损失函数对 $x$ 曲率最小的 $w$, 实现了输入空间的平滑性. 那么如果有其他能够实现平滑性的方法, 理论上就可以替代加噪.

方法之一时直接在损失函数中添加一个梯度惩罚项, 直接**迫使模型在输入点 $x$ 处的损失变化率变小**.

$$
\mathcal{L}_\mathrm{total}=\underbrace{\mathcal{L}(f(\mathbf{x}),y)}_\text{原始损失}+\beta\cdot\underbrace{\|\nabla_\mathbf{x}\mathcal{L}\|_2^2}_\text{梯度惩罚}
$$

此时考虑到权重更新的梯度

$$
\nabla_\mathbf{w}\mathcal{L}_\mathrm{total}=\nabla_\mathbf{w}\mathcal{L}+2\beta\cdot(\nabla_\mathbf{x}\mathcal{L})\cdot\frac{\partial}{\partial\mathbf{w}}(\nabla_\mathbf{x}\mathcal{L})
$$

其中

$$
\frac{\partial}{\partial\mathbf{w}}(\nabla_\mathbf{x}\mathcal{L})=\frac{\partial}{\partial\mathbf{w}}\left(\frac{\partial\mathcal{L}}{\partial\mathbf{x}}\right)=\frac{\partial^2\mathcal{L}}{\partial\mathbf{w}\partial\mathbf{x}}=\mathbf{H}_\mathbf{wx}
$$

这实际上是权重-输入交叉 Hessian 矩阵.

具体来说, 

$$
\frac{\partial}{\partial w_j}\left(\frac{\partial\mathcal{L}}{\partial x_i}\right)=\frac{\partial^2\mathcal{L}}{\partial w_j\partial x_i}
$$

这个交叉偏导衡量了权重参数变化对输入敏感度的影响程度.


一个点可以有很大的梯度但低曲率（远离局部最优的陡坡），也可以梯度为零但有高曲率（局部最优的窄谷底）。理论上两者不完全等价。**但是大部分良好的局部极小点通常是平坦点**, 这些地方也很可能是低曲率的. 更重要的是, 显式惩罚梯度能够强力地将模型参数推向那些损失对输入变化不敏感的区域 (通常是低曲率, 低梯度的) 区域.


## Training with noise is equivalent to Tikhonov regularization

Bishop C M. Neural computation, 1995.

理论上来说, 我们可以直接计算曲率, 进而在损失函数中惩罚曲率, 但是损失函数 $L$ 关于输入 $x$ 的二阶导数难以直接计算, 所以上文我们使用了梯度来近似.

但是 Bishop 的推导依赖于一个关键假设, **添加的噪声 $\epsilon$** 足够小, 这才能够使得损失函数在原始输入点 $x$ 处进行泰勒级数展开, **并忽略高于二阶的项**.

但是我们所添加的噪声并不小, 所以高阶项的存在不能完全忽视, 因此, **并不能完全替代加噪**.

跟澈哥讨论了一下, 澈哥说的有道理: 小噪音的局部扰动提供了平滑性, 大噪音本质则是一种特征淹没, 比小噪音更接近特征选择.

大噪声反应了金融数据的​​高度非平稳性、潜在分布漂移显著、尾部风险（极端事件）严重​​。小噪声只覆盖“小波动”，而​​大噪声模拟了更广泛的未来不确定性场景​​。这本质上是 ​​Distributionally Robust Optimization (DRO)​​ 的需求。



