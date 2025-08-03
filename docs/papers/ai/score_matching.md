# Score matching

> Li Y, Lu X, Wang Y, et al. Generative time series forecasting with diffusion, denoise, and disentanglement[J]. Advances in Neural Information Processing Systems, 2022, 35: 23009-23022.

文章中使用的 score matching 方法称之为 denoising score matching (DSM)，是与其提出的 diffusion process 共同使用的。

> We integrate the multiscale denoising score matching into the **coupled** diffusion process to improve the accuracy of generated results.

之所以使用 DSM 是因为在时间序列生成模型中引入 diffusion probabilistic model 后，生成分布 $p_{\theta}(\hat{Y}^{(t)})$  **倾向于生成加噪后的数据，从而偏离真实数据**，所以通过 DSM 来降低这种不确定性 (de-uncertainty)。

传统 Score Matching 直接估计数据分布的 score $\nabla_{Y}\log p_{\mathrm{data}}(Y)$，当数据为高维时，这一估计需要的**计算复杂度极高**，所以 DSM 通过噪声核 $q_{\sigma_0}(\widehat{Y}|Y)$，

$$
q_{\sigma_0}(\widehat{Y}|Y)=\mathcal{N}(Y,\sigma_0^2I)\propto\exp\left(-\frac{\|\widehat{Y}-Y\|^2}{2\sigma_0^2}\right).
$$

将目标转化为匹配**条件分布**的 score $\nabla_{\widehat{Y}}\log q_{\sigma_0}(\widehat{Y}|Y)$ 从而避免直接估计 $p_{\mathrm{data}}(Y)$，进而**通过梯度学习这一加噪过程的逆向过程，从而恢复出原始分布 $Y$。**


目标函数如下，$\hat{Y}$ 表示模型生成序列，

$$
L_{\text{DSM}}(\zeta) = \mathbb{E}_{p_{\sigma_{0}}(\widehat{Y}, Y)} \left\| \nabla_{\widehat{Y}} \log(q_{\sigma_{0}}(\widehat{Y} \mid Y)) + \nabla_{\widehat{Y}} E(\widehat{Y}; \zeta) \right\|^{2}
$$

公式第一项表示加噪过程梯度，第二项表示能量函数梯度，令二者梯度相等，就可以使得模型学会逆向构建原分布的情况。将这一项经过一通化简就得到了我们所使用的形式

$$
\widehat{Y}_{\mathrm{clean}}=\widehat{Y}-\sigma_{0}^{2}\nabla_{\widehat{Y}}E(\widehat{Y};\zeta).
$$

> [!TIP|label:Energy Function]
> 能量函数 $E(\widehat{Y};\zeta)$ 是一个可学习的函数（如神经网络），用于定义生成模型的为归一化概率分布：
$$
p_\theta(\widehat{Y})\propto e^{-E(\widehat{Y};\zeta)}.
$$
> 能量函数的值越低，表示数据 $\hat{Y}$ 越符合生成模型的分布。
>
> 能量模型通过指数形式将能量函数映射到概率分布
$$
p_\theta(\widehat{Y})=\frac{e^{-E(\widehat{Y};\zeta)}}{Z(\zeta)},
$$
> 其中 $Z(\zeta)=\int e^{-E(\widehat{Y};\zeta)}d\widehat{Y}$ 是归一化常数（配分函数）。
>
> 对概率密度取对数梯度，得到 score 函数
$$
\nabla_{\widehat{Y}}\log p_\theta(\widehat{Y})=-\nabla_{\widehat{Y}}E(\widehat{Y};\zeta).
$$
> 因而可以直接学习能量函数的梯度，避免直接计算 $Z(\zeta)$。这也就是**模型输出的梯度**。

我们的网络使用 DSM 的逻辑略有不同。首先，因为我们是预测任务，所以拿不到 $Y$，因而无法直接对 $Y$ 加噪构建出 $\hat{Y}$，所以通过 $X$ 来得到 $Y$。其次，$X$ 和 $Y$ 的空间可能比较稀疏，所以我们对这两个空间进行加噪。

此时需要注意的是，加噪后的 $Y_t$ 和 $Y$ 本质上属于同一空间的不同分布，预测过程中，

- 第一步使得 $X_t$ 映射到 $Y$ 空间，所以使用 $\hat{Y}_t$ 和 $Y_t$ 作 loss
- 第二步使得 $\hat{Y}_t$ 通过 score matching 在同一空间内调整到 $Y$ 分布，学习逆向降噪过程

在新的框架下，不再对 $Y$ 加噪来填满空间，所以可以理解为只有 $Y$ 附近的空间是密度比较高的，其他的位置密度并不一定高，所以

- 我们希望 $X$ 第一步就能够映射到 $Y$ 的附近，因而第一步中就是通过 $\hat{Y}$ 和 $Y$ 做 loss
- 但是第一步并不能保证就跟 $Y$ 一样了，所以通过第二步 Score Matching 微调，再次使得 $Y$ 和 $\hat{Y}$ 做 loss

跟澈哥交流的过程中，澈哥还说了一个十分有意思的观点，就是使用第一步的预测误差 $\epsilon = ||f(x) - Y||$ 作为 sigma_t 来指导第二步的降噪过程，背后的逻辑就是第一步的误差越大，第二步应该降得越多。有个小问题在于这个 $\epsilon$ 可能不为正态分布，在这种情况下 Score Matching 的适用条件可能不再满足了。












