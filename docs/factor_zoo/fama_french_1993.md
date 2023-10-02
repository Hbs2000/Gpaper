
> The math in real, academic, finance is not actually that hard. Understanding how to use the equations, and see what they really mean about the world, that's hard.
>
> Jonh Cochrane

92年总结了 size 和 book-to-market 两类效应进行了剖析。

93提出了SMB HML 两个因子，正式提出了三因子模型

虽然 BM 是一个估值指标，但依照学术界的惯例还是将其称之为价值因子而非估值因子。

排序法指的是将个股用排序变量进行排序。该方法最核心的思想是：使用个股在该变量上取值的大小来代替个股在该因子上暴露的高低。但是，需要强调的是，这种方法并没有假设变量的取值等于因子暴露，也没有假设这二者之间的满足某种函数关系。仅仅假设变量和因子暴露之间是相关的。以BM为例，该方法认为高BM的股票在围绕BM构建的价值因子上暴露更高，低BM的股票在围绕BM构建的价值因子上暴露更低【保序性】。

这也就解释了为什么该方法仅适用于风格因子，对于其他类型的因子【如宏观经济因子】，由于难以从个股本身的数据出发找到和因子暴露相关的变量，自然也就无法使用这种方法。

然而，排序法仅仅是构建因子模拟组合的一个相对粗暴的方法。因为通过排序法构建的组合难以消除其他变量的影响。

因此，引入了双重排序等等。

一个好的因子，预期收益率应该大于零，除此之外，应能够解释个股超额收益的截面差异

·················

时序回归 截面回归 fama macbeth 回归

时序回归以因子收益率已知为前提

R square tells us that this model explains variation over time (time series regression) (**minor points**)

$\alpha$ being small tells us that the model explain variation across portfolios (**major points**)


当我们说小市值和价值股赚的多，我们是从公司特征的角度出发，而这一描述仅能被称之为是 description of reality，而并非是explanation of reality，小市值或是价值股，都是在说公司特征而非beta（因子载荷），只有当我们说beta时，才是explanation of reality，这其中的区别在于 how you behave 和 who you are。即使是小公司，如果behave like a big company，那么beta应该也很低，而不是只要是小公司就beta高。

··················

## Common risk factors in the returns on stocks and bonds

Fama E F, French K R. ***Journal of Financial Economics***, 1993, 33(1): 3-56.

三篇文章的目的：捕捉因子构造背后的金融直觉

92想要


无论是根据特征构造的风格因子，或是直接使用标准化后的公司特征，都属于 common risk factor 的代理

根据公司特征构建的组合称之为 mimicking portfolio，因为其想要mimic the underlying risk factor

有时因子可以捕捉variation，但并不能捕捉收益率，例如在零附近波动的的因子，均值为零但是标准差很大。这一因子在回归中会很显著，同时R方也会很高，但是如果在SML的视角下来看，回归系数 $\beta$ 并不能解释风险溢价，因为斜率 $\lambda$ 接近于0。这两项其实也对应了 Gu et al. 等所提出的total R方和predict R方

对于仅能解释波动而无法解释收益率的因子，在回归中呈现的结果会是：

- 时序回归时，因为能够解释波动，因此R方会很高，截距项会很低
- 而当截面回归时【即对各类资产收益率做平均后回归】，其风险溢价接近零，对预期收益率解释为零【如果仅为但单因子回归则为时序回归中的截距项】

但是这并不代表此类因子就是 irrelevant，因为像是 TERM 此类反应discount-risk的因子，与商业周期有关，在经济繁荣时底，在经济低谷时高，对于DEF，在商业不景气时违约风险高，而在经济蓬勃发展时违约风险低。

~~~~~~~~~~~~~~~~~~~~~

如何看待收益率？

处理公司特征与因子的逻辑

BE/ME 衡量了 distress effects

Fama这两篇文章尽管很著名，但都没有找到背后的原理，也就是说，仍旧是数据的结果，类似于bryzgolova所提出的样本外夏普比率更高，只是因为这种方法属于线性，可解释性天然强一些罢了。


GAN 这一篇也是从test asset的角度出发，但是是从GMM 和 $Emr=0$ 得出的，并不是直接看样本外夏普比率，因此相比于树更加具有经济学含义。

聚类的算法中能不能加入无套利限制？

-------------------------------

GAN：通过非参方法构建SDF的结构，通过样本外夏普比率这一目标函数构建了test asset【Test asset和SDF这二者有什么不同吗】

Bryzgalova：




