# Math requist

Lipschitz continuity 用于确定与真实极值之间的距离

gradient descent 和 SGD，对于复杂的neural network，很多时候不可能要求convex，只能求gradient，进行backpropogating，只能通过调参使得 numerically 达到一个不错的值



为什么会有SGD，而不是直接求导，SGD不是完整的做一个GD：DL的求导是

gradient descent是通过梯度更新参数，有时候得不到gradient，就有subgradient

因为subgradient是一个集合，因此最后随便选一个用于计算可能就不下降

能下降又算得准：proximal gradient method，并且即使一部分可微，一部分不可微，仍然可以计算

什么问题需要用gradient descent




