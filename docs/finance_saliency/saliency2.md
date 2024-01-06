## Finding the Secret of Image Saliency in the Frequency Domain

Jia Li<sup>1</sup>, Ling-Yu Duan<sup>2</sup>, Xiaowu Chen<sup>3</sup>, Tiejun Huang<sup>4</sup>, Yonghong Tian<sup>5</sup>, IEEE transactions on ***pattern analysis and machine intelligence***, 2015

1. *Member, IEEE, School of Computer Science and Engineering, Beihang University*
2. *Member, IEEE, School of Electronics Engineering and Computer Science, Peking University*
3. *Member, IEEE, School of Computer Science and Engineering, Beihang University*
4. *Senior Member, School of Electronics Engineering and Computer Science, Peking University*
5. *Senior Member, School of Electronics Engineering and Computer Science, Peking University*


目前研究 Image Saliency 的文献，均是在频域上进行操作的，但是并不清楚频域中的哪一部分对于识别 Saliency 是最关键的。

本文的第一部分，通过多个 empirical experiment 发现 **the phases of intermediate frequencies** 是最重要的部分。其中，**实数和虚数部分的正负极为重要**。为了解释这一结论，文章从 **the template-based contraset computation** 的角度对 discrete Fourier transform 做了重构。

第二部分：是通过这些实证经验，构造 Saliency detector。自称是第一个用机器学习方法在 frequency domain 解决 visual saliency 的问题。

第三部分就是实证模型对比。此处需要强调的是，文章中反复提及一点:

> *the prior knowledge obtained through similar scenes viewed before plays an important role in separating targets and distractors*

其实就是对 input 做了 ICA，去除了 redundant 成分。

### Literature

Three branches of visual saliency modeling:

1. **Objectness proposal generation**: focuses on locating "objects", including both targets and distractors.

2. **Fixation prediction**: aims to roughly pop-out only targets adn inhibit distractors

3. **Salient object segmentation**: proposes to exactly segment the closed contours of salient targets.


有许多模型是直接在 Spatial or spatiotemporal domain 进行的。如果要在 frequency domain 中进行操作，一般分为如下三个步骤：

(1) applying discrete Fourier transform (DFT) 

(2) **modulating** the frequency spectrum

(3) generating saliency map through inverse DFT/DCT

在频域领域的文章中，poineer work 就是这个 notes 的第一篇，利用 residual 来识别 Saliency。在此基础上，Guo and Zhang 提出了两个**非常重要的改进**：

1. use **only the phase spectrum** of image intensity (and unity magnitude) for saliency detection

随后，Hou, Harel, and Koch (2012, PAMI) 证明了 discrete Cosine transform 的系数在 detect saliency 中起到了非常重要的作用

2. represented an image as a **quaternion** comprising of four feature channels (i.e.,intensity, red/green and blue/ yellow color opponencies, and motion). 【Notes 第二篇文章】

> Thus image (or video) saliency can be simultaneously estimated through the frequency spectrum obtained by applying HFT to multiple features


Among the two improvements, **the latter one has much stronger impact than the former one**, it becomes very popular to represent an image as a quaternion in recent studies


### The secret of Saliency

As discussed above, both *spectral amplitude* and *phase* can contribute to the detection of salient target

#### Qualitative Study

the objective of saliency prediction is to generate a saliency map $S$ for an input image $I$ that perfectly approximates its fixation density map $G$

$$
\begin{equation}
    I\Rightarrow S\rightarrow G,
\end{equation}
$$

在频域上的表达为：

$$
\begin{equation}
    \mathscr{F}[I]\Rightarrow\mathscr{F}[S]\to\mathscr{F}[G],
\end{equation}
$$

也就是说，在频域上，$S$ 的振幅和相位都要靠近 $G$:

$$
\begin{equation}
    \mathcal{A}(F[S])\to\mathcal{A}(F[G]),\mathcal{P}(F[S])\to\mathcal{P}(F[G]),
\end{equation}
$$

<div align='center'>

![](../Courses_in_SUSTech/image/20231113PP4.png)
</div>

集合 $I$ 中的东西是最拉的，$G$ 里的东西是最好使的，那么最拉的振幅配上最猛的相位和最拉的相位配上最猛的振幅，一下就能看出到底是谁在起作用，结果显示：**是相位在起作用**。

#### Quantitative Study




#### A Template-Based Reinterpretation of DFT

对于给定的图像 $I$，其 complex-valued Fourier coefficient at $u, v$ 估计系数如下：

$$
\begin{equation}
    F(u,v)=\sum_{x=0}^{N-1}\sum_{y=0}^{N-1}I(x,y)e^{i\theta},\theta=\frac{-2\pi(ux+vy)}N,
\end{equation}
$$

将 $e^{i\theta}$ 通过欧拉公式展开，则 $F(u,v)$ 实部与虚部可以写为如下形式：

$$
\begin{align}
    \begin{gathered}
    \Re(u,v)=\sum_{\cos\theta\geq0}\operatorname{cos}\theta I(x,y)+\sum_{\operatorname{cos}\theta<0}\operatorname{cos}\theta I(x,y), \\
    \begin{aligned}\Im(u,v)=\sum_{\sin\theta\geq0}\sin\theta I(x,y)+\sum_{\sin\theta<0}\sin\theta I(x,y).\end{aligned} 
    \end{gathered}
\end{align}
$$

这也正是说明了，傅里叶变换的系数可以写为 **template-based contrasts**。

进一步地，实部与虚部能够通过一些 template 表示：

$$
\begin{equation}
    \begin{aligned}\Re(u,v)&=\left\langle I\otimes\mathcal{T}_{uv}^{\Re+}\right\rangle-\left\langle I\otimes\mathcal{T}_{uv}^{\Re-}\right\rangle,\\\Im(u,v)&=\left\langle I\otimes\mathcal{T}_{uv}^{\Im+}\right\rangle-\left\langle I\otimes\mathcal{T}_{uv}^{\Im-}\right\rangle,\end{aligned}
\end{equation}
$$

其中，

$$
\begin{align}
\begin{gathered}
    \mathcal{T}_{uv}^{\Re+}(x,y) =\max(\cos\theta,0), \\
    \mathcal{T}_{uv}^{\Im+}(x,y) =\max(\sin\theta,0), \\
    \mathcal{T}_{uv}^{\Re-}(x,y) =\max(-\cos\theta,0), \\
    \mathcal{T}_{uv}^{\Im-}(x,y) =\max(-\sin\theta,0). 
\end{gathered}
\end{align}
$$

也就是说，这四个 templates 将 input 分为了两个**加权对比组**。

<div align='center'>

![](../Courses_in_SUSTech/image/20231113PP5.png)
</div>


### Saliency Detector

#### Principles for detector

(1) Multiple complementary feature channels are preferred to fully utilize the input visual stimuli.

(2) Both spectral amplitude and phase should be modulated to reach the best performance. 【filter 的使用】

(3) **Phase modulation helps to locate the salient targets, and amplitude modulation helps to clean up probable noise**

(4) **Intermediate frequencies** should be emphasized, and the lowest and highest frequencies should be suppressed

(5) Fourier coefficients can be adjusted with respect to their neighbors for encoding template-based contrasts at similar orientations and scales.

> 这些都是在图像领域的实证之谈，那么在金融领域，是**无法照搬套用**的。

$$
\begin{equation}
    \begin{gathered}
    F_{I_{c}} =\mathcal{N}(\mathscr{F}[I_{c}]\otimes H_{bh}),~\forall c\in\{1,\ldots,C\}, \\
    F_{I_{c}}^{*} =\mathcal{N}\bigg(F_{I_c}*H_p^c\bigg),\forall c\in\{1,\ldots,C\}, \\
    \text{S} =\sum_{c=1}^{C}\bigg|\mathcal{F}^{-1}\bigg[\mathcal{N}\bigg(F_{I_{c}}^{*}\otimes H_{bl}\bigg)\otimes H_{bl}\bigg]\bigg|^{2}, 
    \end{gathered}
\end{equation}
$$


