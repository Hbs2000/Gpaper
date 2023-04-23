# Viewing the Business Through the Financial Statements

The transaction between debtholders and shareholders and the firm are the firm's financing activities.

In this chapter, we **reformulate** the statements in a way that aligns the statements with business activities.

**reformulation的关键在于seperate operating and investment activities from financial activities**

- Cash flow statement: indentify cash flow of a business
- Balance sheet: indentify operating and financing assets and liabilities
- Income statement: identify operating and financing income
- Financial statement: articulate to present a picture of the business


## The reformulation of Statements

### The Cash flow

<mark>

<div align = 'center'>

![](../image/20230327FS1.png)
</div>

$$\begin{aligned}
\text{F} &= \text{Net principal payments + net interest paid} \\
\text{d} &= \text{Common dividend + share repurchases}- \text{share issues}
\end{aligned}
$$

就债务端来说，公司有钱的时候可以是债券的购买方，没钱的时候可以是债券的发行方。

除了融资活动，公司还进行了投资活动，进一步**补全**上图：

<div align = 'center'>

![](../image/20230419FS1.png)
</div>

投资活动 $\bm{I}$ 指的是投资于营运资产（operating assets），而为了进行投资活动，公司需要卖掉金融资产。箭头是**双向的**，因为公司也可以卖掉营运资产来购买金融资产。

这些营运资产会产生收益，收益减去成本【工人工资等】的现金流就称为营运现金流（cash flow from operations） $\bm{C}$。


根据上图，引出了非常重要的一个等式：

**The sources and uses of cash equantion 【always true】**
</mark>

这个等式永远成立。

如同这个等式的名字，讲的就是钱从哪来，要往哪去。由营运活动产生的现金流减去投资到营运资产里的钱【Free cash flow】，剩下的钱用于发放给股东和还债【也有可能是不足的钱由发债和发股票来筹资补足】。


$$\begin{aligned}
\text{C - I} &= \text{d + F} \\
\text{the sources} &= \text{the uses}
\end{aligned}
$$



根据cash equation，假设不减少d的情况下，能够得到 **the treasurer's rule**

> [!NOTE]
> 这里的d指的是net dividend，包括Cash dividend，share repurchases和share issues等。
>
> 同样，F指的是net payments to debtholders and issuers，所以既包括利息收入与指出（i），也包括债券的购买与发行。
>
> 当现金流偿付完利息后不足以支付net dividend，就要发行债券，反之同理。

$$\begin{aligned}
& \text{If C - I - i > d, then lend ro buy down own debt} \\
& \text{If C - I - i < d, then borrow or reduce lending}
\end{aligned}
$$

根据 Treasurer's rule，reformulate cash flow statement为：

<div align = 'center'>

![](../image/20230327FS5.png)
</div>

**Example**

<div align = 'center'>

![](../image/20230419FS2.png)
</div>



### The Balance sheet

<div align = 'center'>

![](../image/20230327FS2.png)
</div>

在报表中，一般将资产和负债分为短期和长期，这种划分对于credit analysis比较有用，但是对于权益分析【equity analysis】来说，分为operating和financial更加合适。

可以理解为：operating assets or liabilities面向消费者和供应商；financial assets or liabilities面向资本市场。


为了进一步将financial activities与其他的operation区分开，可以reformulate为：

$$\begin{aligned}
\text{OA + FA} &= \text{OL + FO + CSE} \\
\text{rearranged, OA - OL + FA - FO} &= \text{CSE}\\
\text{Net operating assets (NOA)} &= \text{OA- OL} \\
\text{Net financial assets (NFA)} &= \text{FA - FO} \\
\text{thus, CSE} &= \text{NOA + NFA}
\end{aligned}$$

可理解为是：**所有者权益投资到了净营运资产和净金融资产上**。

<div align = 'center'>

![](../image/20230327FS4.png)
</div>

通常情况下，$\text{NFA (Assets)}$ 为负数，因此也被写为 $\text{NFO (Obligation)}$：
$$
\text{CSE = NOA - NFO}
$$



### The Income sheet

Typical Income sheet

<div align = 'center'>

![](../image/20230419FS3.png)
</div>

同样将Income sheet按照operating和financing reformulate【其实反映在公式中也就是简单移项】：

<div align = 'center'>

![](../image/20230419FS4.png)
</div>

### Relations between reformulated statements

完整的operating activities还包括interaction with customer and supplier，如下图：

<div align = 'center'>

![](../image/20230327FS3.png "Fig 1")
<br>

**Fig 1**
</div>

OE指的是operating expense，OR指的是operating revenue，OI为operating Income。OI为正则代表公司价值增加，反之价值减少。

OE和OI并不代表现金流【cash flow】，而是价值流【value flow】，相应地，为了更好的衡量价值流动，引入了Accrual accounting。同样地，interest income and expense也通过accrual来衡量


### The drivers for Cash Flow and Dividend

在Fig 1下方展示了三者之间的联系，这种联系不仅反映了其相关性，也写明了各项目背后的驱动因素【driver】是什么。

1. Free cash flow is what’s left over from OI after adding to the balance sheet

$$\begin{aligned}
\Delta\text{NOA = OI - (C - I)} \\
\text{C - I = OI - } \Delta \text{NOA}
\end{aligned}$$

2. Free cash flow is applied to pay $\text{NFE}$, reduce debt and pay dividends

$$\begin{aligned}
\Delta\text{NFO = NFE - (C - I) + d} \\
\text{C - I = NFE - } \Delta \text{NFO + d}
\end{aligned}$$

3. Net dividend is the cash left over from free cash flow after paying $\text{NFE}$ and reducing debt.
$$\begin{aligned}
\Delta\text{NFO = NFE - (C - I) + d} \\
\text{d = }\text{(C - I) - NFE + } \text{NFO}
\end{aligned}$$


## The big picture

<div align = 'center'>

![](../image/20230327FS7.png)
</div>

> [!ATTENTION|label:Typo]
> 第三行 $CSE_{t-1}$ 后应为加号

### What Generates Value?

根据公式：
$$
CSE_t = NOA_t - NFO_t
$$

带入得：
$$\begin{aligned}
CSE_t &= NOA_{t-1}+OI_t - (C_t-I_t)-NFO_{t-1}+(C_t-I_t)-NFE_t-d_t \\
&= NOA_{t-1}-NFO_{t-1}+OI_t-NFE_t-d_t \\
&= CSE_{t-1}+Earn_t-d_t
\end{aligned}$$

Clean Surplus 【对应dirty surplus】

**现金流 $(C_t-I_t)$ 并不对股东产生价值**，因为其减少NOA的同时也减少了NFO，在计算中被抵消掉

**真正影响股东价值**的是 $OI_t-NFE_t$，分别对应operating和financial activities

**Example**

<div align = 'center'>

![](../image/20230327FS8.png)
</div>


## Concept Questions

*A firm has positive free cash flow and a net dividend to shareholders that is less than free cash flow. What must it do wi th the excess of the free cash flow over the dividend?*

Refer to the cash conservation equation: $\text{C} – \text{I} -\text{d = F}$. The firm **must** pass out the excessof free cash flow after dividends to net debtholders, by buying down to its own financial obligations or by buying others’ debt as a financial asset.




