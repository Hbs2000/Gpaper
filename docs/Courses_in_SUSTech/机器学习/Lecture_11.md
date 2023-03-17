# Sampling Methods

对于大多数实际使用的模型来说，很难获得精确的推断结果，因此往往不得不诉诸于一些近似方法（approximate inference）。


 


## Monte Carlo
本质是随机抽样

通过点估计  


### Rejection Sampling
容易实现但效率不高，如果涵盖比例很低，就会导致拒绝的比例很高而抽样效率很低。在高维空间中进行抽样时，即使二者很接近，

> [!ATTENTION|label:维度灾难]
> 当维度不断升高的过程中，超立方体的体积不变，但相切超球体的体积趋近于0。


### Importance Sampling





## Markov Chain
平稳要说一下，使用该平稳分布进行近似数值计算



给出初始概率分布以及状态转移矩阵P，最终都会实现稳定的概率分布，也即到达一定次数后，概率不再变化。

既然稳定了，也就是一种分布。

问题在于如何得到这个转移矩阵。

detailed balance



## MCMC

The goal of MCMC is that we want to sample from distribution p or approximate an expected value

分布非常复杂，不可能得到解析解。

在高维空间下，我们不会有很好的intuition






