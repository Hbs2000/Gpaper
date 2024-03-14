# Attention Is All You Need

NIPS2017, citation: **100k+**

attention $\neq$ transformer




layerNorm 与 batchNorm，为什么在变长的应用中不使用batchNorm


layerNorm 是对样本做标准化，batchNorm 是对 feature


当 $d_k$ 维度比较大的时候，容易出现其中某一个值很大，这样 softmax 后这个值就会更加接近于 1，其他值接近于 0，但是这种接近并不是我们想要的接近，因此 除以 $d_k$ 减弱这种影响。

mask 主要是用来避免在 $t$ 时刻看到 $t$ 时间以后的东西


多头注意力：类似于卷积可以卷许多次，每一次卷积都可以得到一个 feature map，另一方面也是因为单纯 self-attention 这个机制本身没有太多参数可学，投影过程也是增加参数过程


attention 的输出是 value 的加权和，并不包含时序信息，因此任何一个序列打乱顺序，attention 最后出来的值也是一样的。

attention 对于模型的假设更加少，所以需要更多的训练参数才能达到与 CNN RNN 同样的效果，所以基于 Transformer 的模型都特别大，特别多



