# Style investing in fixed income

Jordan Brooks<sup>1</sup>, Diogo Palhares<sup>1</sup>, Scott Richardson<sup>1,2</sup>

1. *AQR Capital Management LLC*
2. *London Business School*

> 将 equity 中的 Style investing 应用到 Fixed income 中。

**Conclusion**

1. Both within and across government and corporate bonds, strong evidence of **low correlation** across style portfolios
2. Fixed income style portfolios can be built in such a way they do not give exposure to **traditional market risk**, nor do they give exposure to equity style portfolio returns.
3. Very little sensitivity of fixed income style portfolio returns to **various macroeconomic state variables** that investors are typically concerned about (shocks to inflation, shocks to economic growth, real yields, liquidity and volatility).

## Measuring styles in Fixed income

**Value**

*Value is the tendency for relatively cheap assets to outperform relatively expensive assets.* 

Thus, for value portfolios, we need a credible measure of 'fundamental' value to compare against marekt prices.

We measure market 'prices' as 

- yields in the case of government bonds
  - Specifically, we compare nominal yields against maturity matched inflation expectations.
- credit spreads in the case of corporate bonds

> Credit spread is the yields minus risk free rate of bonds, usually the government bonds with same maturity.
>
> Because for government bonds, we only needs to care about the inflation, but for coporate bonds we also concern about the default risk, which is the main part of yields.

Goverment bonds with, relative to their peers, higher (lower) real yields are cheap (expensive).

For corporate bonds we compare credit option adjusted spreads against two fundamental anchors designed to capture the 'risk' that the company may migrate to a poorer credit quality.

1. The first fundamental anchor is a structural model which measures the bond's "distance to default" reflecting the number of standard deviations the asset value is away from the default threshold.
   - Correia, M., S. Richardson and İ. Tuna. “Value Investing in Credit Markets.” *Review of Accounting Studies* 17 (3) (2012), pp. 572-609
2. The second fundamental anchor is an empirical model based on a regression of the spread on duration, rating and return volatility.
   - Israel, R., D. Palhares, and S. Richardson. “Common factors in corporate bond returns.” Forthcoming, *Journal of Investment Management* (2018)

In both cases a corporate bond is deemed to be cheap (expensive) when the credit spread is high (low) relative to the respective fundamental anchor.


**Momentum**

*Momentum is the tendency for an asset’s recent performance to continue in the near future.*

Measures designed to reflect recent performance can be price and **non-price based**.

> See Brooks, J. “A half century of macro momentum.” Working paper, AQR Capital Management 2017. for a discussion of non-price, or fundamental, based measures of momentum within global macro asset classes.

For the sake of simplicity we only consider an asset's own momentum or that of a closely related asset. For government bonds we use the prior 12 month excess return.

For government bonds we use an equal weighted **combination** of the bond's prior 12 month excess returns and (for public issuers) the stocks's prior 12 month returns.

**Carry**

*Carry is the tendency for higher yielding assets to outperform lower yielding assets.*

While value tends to profit if **the prices revert to fundamentals** and momentum tends to profit if **the recent trends persist into the future**, carry meansures expected returns if **nothing happens but for the passage of time**.

> Ilmanen, Antti. Expected Returns, (2011), Wiley. provides a good summary of relevant literature here.

For government bonds we use the term spread, which is the simple difference between the bond's nomial yield and the local short-term yield, which measures the expected return to a goverment bond assuming the yield level remain unchanged.

For coporate bonds we use the bond's option-adjusted spread (OAS) versus Treasuires, as estimated by Bank of America Merrill Lynch, which measures the expected return to a corporate bond assuming the spread level remains unchanged.


**Defensive / Quality**

*Defensive or (quality) is the tendency of safer, lower-risk assets to deliver higher riskadjusted returns than their low quality, higher risk counterparts.*

Measures of 'safety' or 'high quality' can be market based or fundamental based. For government bonds we use effective duration as our measure. Specifically, within each country we buy short-dated bonds and sell a duration-equivalent amount of long-dated bonds.

For corporate bonds we alse favour low duration, but we also include two additional indicators based on profitablity (gross profits over assets) and leverage (measured by the ratio of net debt to the sum of net debt and market equity).






