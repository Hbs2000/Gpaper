# Forest through the Trees: Building Cross-Sections of Stock Returns
Svetlana Bryzgalova, Markus Pelger, Jason Zhu, Working paper, 2021
1. *London Business School, Department of Finance*
2. *Stanford University, Department of Management Science and Engineering*
3. *Stanford University, Department of Management Science and Engineering*


## 什么解释了预期收益率？

***What explains expected returns?***

这个问题背后有两层含义：

1. 要解释谁的预期收益率？测试资产一般选取截面排序形成的组合收益率
2. 用什么模型来解释？


大多数文献都关注第一个问题，实际上，第二个问题也十分重要。原因如下：

1. 除非选取的测试资产可以张成（span）SDF，否则即使能够解释这些测试资产，也不能说明模型的可靠性
2. 测试资产不仅可以用于检验模型，还可以用来构建交易组合（building blocks for constructing tradebale risk factors）

因此，mis-specified test asset 不仅影响了SDF的构造，也影响了其评价模型的能力。

过往文献最常使用的特征排序组合无法张成SDF，因此基于这些方法做出的model evaluation实际上也是不可靠的。这些截面排序的组合并不能反映出众多特征的联合影响——**受限于维度灾难以及对交互作用的忽略**。

通常的做法是将许多排序形成的组合堆在一起，而这并不能解决上述问题，并且会引起新的麻烦：因为这些组合都是基于同一个投资域选取的，所以存在大量的重复组合以及对于同一种风险的重复构造。

出于对这三种问题的考虑：
1. 交互作用（complex interactions）
2. 维度灾难（curse of dimensionality）指的是25个组合太多还是用于形成这些组合的因子太多
3. 组合重复（repackaging and duplication）

文章提出了AP tree model（Asset Pricing Trees）。

### AP trees

AP trees具有很好的可解释性，构造出的组合充分分散化，最重要的是，最终AP trees组合能够张成SDF。

**Two key elements：**
1. 类似于条件排序构造组合
2. **根据SDF的限制条件剪枝（pruning）**

当构造出树结构后，再根据限制条件进行剪枝。但此处的剪枝与机器学习方法中的剪枝有本质区别：机器学习方法中根据local information（如mean impurity decrease），即仅对比父节点和子节点之间的信息，而本文则是在均值方差优化的框架下，考虑所有的节点，因为这些节点都是投资组合，来观察哪些节点组合在一起能够得到最高的夏普比率。

最后，为例避免过拟合，文章还实现了**对方差和均值的收缩**。因此也算是generalization of Kozak, Nagel, and Santosh (2020)。

### Evaluation metrics <!-- {docsify-ignore} -->

由于重复资产的存在，传统评价指标如absolute pricing errors往往会夸大模型的表现。

本文提出使用样本外解释SDF的能力来评价模型，得到更为准确的结果。


### The role of Machine Learning <!-- {docsify-ignore} -->

大多数机器学习算法通过两步来构建投资策略：
1. 通过算法提取预测收益率的信号
2. 通过这些信号来构建投资组合，如long short或均值方差优化

**然而，这两步实际上应该合并为一步，也即，直接找到对经济学问题最相关的信号，而非仅与收益率相关。**

> *However, we strongly believe that these two steps should be merged together; that is, machine learning techniques should extract the signals that are the most relevant for the overall economic problem, not just return prediction.*

> [!NOTE]
> 这一点与Hierarchical Bayesian、Shrinking the cross section、RP-PCA的观点是一致的。

文章后续也做了对比，仅提取与收益率相关信号的模型表现远不如考虑经济学问题的模型。



### Closely Related Literature

Factor zoo实际上是基于统计和经济学模型找一些可以张成SDF的基础资产（basis assets）。

回答Factor zoo的文献可以被分为以下三类：

1. **对特征组合做降维处理，最终得到少数几个因子或SDF**


- Lettau and Pelger (2020) 
- Kelly, Pruitt, and Su (2019) 
- Fan, Liao, and Wang (2016) 
- Kozak, Nagel, and Santosh (2020) 

PCA是这一类文献中最常用的方法，但由于这些方法是在已有的投资组合中提取信息，就会存在上述提及的问题。而本文是在全新的投资组合中提取信息，这些组合有更多的信息量。

1. **仅提取特征和收益率之间的关联，而不假设风险模型或无套利限制**


- Freyberger, Neuhierl, and Weber (2020) 
- Gu, Kelly, and Xiu (2020b)
- Moritz and Zimmerman (2016) 
- Rossi (2018) 

本文不仅着眼于收益率，而是从SDF入手。

1. **在不假设股票和特征之间关系的前提下 (Nonparametric)估计条件SDF**


- Chen, Pelger, and Zhu (2022)
- Gu, Kelly, and Xiu (2020a)

本文在基于特征估计条件SDF的同时，保证了模型的**可解释性**。

特别地，对于Kozak, Nagel, and Santosh (2020)，其仅仅对协方差矩阵进行了收缩，然而本文在此基础上，对收益率均值也施加了收缩。这一收缩有极大的意义，**因为样本均值中包含了大量的估计误差，而尽管其绝对数值很大，但其中有很大一部分是由噪声导致的，而不是数据的本质特征**。

根据Garlappi, Uppal, and Wang (2007)的框架，可以证明这个问题**等价**于：面临期望收益、波动率、以及投资机会夏普比率的联合不确定性的条件下，求解模糊厌恶的投资者的最优投资组合。而Kozak, Nagel, and Santosh (2020)仅仅是这一框架下的一个特例。












  