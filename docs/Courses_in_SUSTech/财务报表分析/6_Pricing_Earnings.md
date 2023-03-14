# Accrual Accounting and valuation: Pricing Earnings

本章仍然是通过该公式进行估值，但是视角从PB转向PE。
$$
\text{Value = Anchor + Extra Value}
$$

***The big picture for this chapter***

To price earnings, one thinks of earnings growth: <u>more growth, higher P/E</u>

But:  Beware of paying for growth
- Only pay for growth that adds value 【我们只需要pay for 超过正常增长的部分】
- <u>Growth is risky</u>:  Beware of paying for risky growth 【有些增长是不可持续的，竭泽而渔式的】

**Abnormal earnings growth** is the metric that protects from paying too much for growth

## The concept behind P/E ratio


## From PB to PE
在PB valuation中，我们可以通过计算Residual Earning并折现，而在PE Valuation中，我们通过计算RE的变化来得到估值。
<div align = 'center'>

![](../image/20230314FS1.png)
</div>

$$
V_0^E = {1\over \rho_E -1} \Big[ EPS_t + {\Delta RE_2\over \rho_E}+{\Delta RE_3\over \rho_E}{\Delta RE_4\over \rho_E}+{\Delta RE_4\over \rho_E}  \Big]
$$

### Change in Residual Earnings and Abnormal Earnings Growth

$$\begin{aligned}
\text{V} &= \text{Book Value + PV of Residual Earnings} \\
&= \text{Capitalized forward earnings + PV of Changes in Residual Earnings}
\end{aligned}
$$

实际上，这二者是等价的
$$
\text{Change in Residual Earnings = Abnormal Earnings Growth}
$$

Abnormal Earnings Growth (AEG), which is the center for P/E valuation, is **growth in earnings over the required growth rate**

## Saving Account

<div align = 'center'>

![](../image/20230314FS2.png)
</div>

在这个例子中，每年分红并不会影响对于该账户的估值，即使而这个Earning Growth Rate和Book Value增长不同。原因就在于Cum Dividend Earnings。

### Cum dividend earnings

Cum dividend earnings代表着不仅考虑earning的growth，也考虑前一年的分红再投资所能产生的报酬。这样二者就是等价的。

<div align = 'center'>

![](../image/20230314FS3.png)
</div>

***Normal Earnings***

Normal Earnings 相对的就是abnormal，也就是说不存在超出要求报酬之外的收益，earnings growing at the required rate of return:
$$
\text{Normal Earnings}_t = \rho_E \text{Earnings}_{t-1}
$$

For the savings account:
$$
\text{Normal Earnings}_{2014} = 1.05 \times 5 = 5.25
$$


***Abnormal Earnings Growth (AEG)***

Abnormal Earning Growth 与 Residual Earnings有着close relation：
$$\begin{aligned}
\text{AEG}_t &= \text{RE}_t - \text{RE}_{t-1} \\
&= [Earn_t+(\rho_E-1)d_{t-1}]-\rho_E Earn_{t-1} \\
&= \pmb{\text{Cum-dividend earn}_t - \text{Normal Earn}_t}
\end{aligned}$$

通过简单推导即可得出。


### Lessons from the Savings Account

<div align ='center'>

![](../image/20230314FS4.png)
</div>

<mark>

### Exercise
</mark>

<div align ='center'>

![](../image/20230314FS5.png)
</div>

这里我们引入了Cum-dividend earnings, Normal earnings, abnormal earning growth的计算

<div align ='center'>

![](../image/20230314FS6.png)
</div>


## A Model of the Forward P/E

$$
\text{Value of equity = Capitalized forward earnings + Extra value for abnormal earnings growth}
$$
根据上述等价关系，value of equity也有两种等价表达：
$$\begin{aligned}
V_0^E &= {1\over \rho_E-1}\Big[ Earn_1+{AEG_2\over \rho_E}+{AEG_3\over \rho_E^2} +{AEG_4\over \rho_E^3}+\cdots \Big] \\
&= {1\over \rho_E-1}\Big[ Earn_1+{RE_2\over \rho_E}+{RE_3\over \rho_E^2} +{RE_4\over \rho_E^3}+\cdots \Big]
\end{aligned}$$

当abnormal项为0，也就得到了normal PE：
$$
{V_0^E \over Earn_1} = \text{Normal  PE} = {1\over \rho_E-1} = {1\over \text{required return}}
$$

### Cum-dividend Earnings Growth Rate

$$
G_t = {\text{Cum dividend earnings}_t \over \text{Earnings}_{t-1}}
$$

> [!NOTE]
> $$
> \pmb{NOT} \quad {\text{Cum dividend earnings}_t \over \text{Cum dividend earnings}_{t-1}}
> $$

根据$ G_t $的定义，AEG还有另一种表达：

$$\begin{aligned}
AEG_t &= \text{Cum dividend earnings}_t - \text{Normal earn}_t \\
&= \text{G}_T \times \text{Earnings}_{t-1} - \rho_E \times \text{Earnings}_{t-1} \\
&= [\text{G}_T-\rho_E]\times\text{Earnings}_{t-1}
\end{aligned}$$












