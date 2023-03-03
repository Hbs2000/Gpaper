# Cash Accounting, Accrual Accounting, and Discounted Cash Flow Valuation

- What is the **dividend discount model**?  Does it work? 
- What is the **discounted cash flow model**? Does it work? 
- What is the difference between cash accounting and accrual accounting?
- What type of accounting best captures value added in operations: **cash accounting** or **accrual accounting**?


## Dicount Dividend Model（DDM）

DDM就是根据discount rate把未来红利全部折现。
$$
\rho (discount\ rate) = 1+r(required\ return)
$$

### Perpetuity

***A perpetuity is a constant stream that continues without end.***

**Constant dividend**

$$
V^E = {1\over \rho^E -1}
$$


**Dividend with Growth $g$**
$$
V^E = {1\over \rho^E - g}
$$


**PROBLEM**
- Dividend policy can be arbitrary and not linked to value added
- Dividends paid before $T$ reduce $P_T$ to leave the present value unaffected

> [!TIP|label:The dividend conundrum]
> Equity value is based on future dividends, but forecasting dividends over finite horizons dose not give an indication of this value

**Conclusion**: Focus on creation of wealth rather than distribution of wealth  

### Analysis of DDM
<div align = 'center'>

![](../image/20230302FS1.png)
</div>

## Discount Free Cash Flow Model（DCF）

$$
FCF = OCF-CAPX
$$

> [!TIP|label:FCF]
> Free Cash Flow: ***The part of cash flow from operations that is free after the firm reinvests in new assets***

**Capital expenditure (CAPX)** are funds used by a company to acquire, upgrade, and maintain physical assets such as property, industrial buildings, or equipment. 

CAPX can be found in the cash flow from investing activities, such as capital spending, purchases of property, plant, and equipment (PPE), acquisition expense, etc.

### Basic equations

$$\begin{aligned}
V^E &= V^F - V^{ND} \\
&= {C_1 - I_1 \over \rho_F}+{C_2 - I_2 \over \rho_F^2}+......+{C_T - I_T \over \rho_F^T} +{CV_T\over \rho_F^T}- V^{ND}
\end{aligned}$$

**CV**: continuing value

**Net Debt**: the debt firms hold as liabilities less debt investments that firms hold as assets

***Calculating CV***

**Constant Free Cash Flow**
$$
CV_T = {C_{T+1} - I_{T+1}\over \rho_T-1}
$$

**Free Cash Flow with growth $g$**
$$
CV_T = {C_{T+1} - I_{T+1}\over \rho_T-g}
$$
> [!NOTE|label:注意]
> 这里用的是下一期自由现金流，当给出本期现金流以及增长率时，**下一期现金流为二者的乘积**


### Process

- Forecast free cash flow to a horizon, e.g., 5 years
- Discount the free cash flow to present value
- Calculate a continuing value at the horizon with an estimated growth rate
- Discount the continuing value to the present
- Add 2 and 4
- Subtract net debt

<mark> ***Example*** </mark>

***Example***

