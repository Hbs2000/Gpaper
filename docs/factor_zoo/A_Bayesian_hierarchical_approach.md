# Factor investing: A Bayesian hierarchical approach

Guanhao Feng<sup>1</sup>, Jingyu He <sup>1</sup>

1. *City University of Hong Kong*


- estimates the conditional expected returns and residual covariance matrix **jointly**
- The hierarchical prior allows the modeling of different assets separately while **sharing information** across assets
- the stochastic discount factor constructed by our BH approach can explain many risk anomalies

- what is estimation risk
- hierarchical因为是different asset所以才hierarchical吗 
- what is model heterogeneity

By contrast, traditional frequentist statistical approaches or modern machine learning predictive methods fail to evaluate such prediction risk properly. The estimation risk issue dramatically increases when investors allocate funds among multiple assets due to the high dimension of the parameter space.


**If returns are unpredictable, the mean–variance efficient portfolio is time-invariant**. Therefore, the econometric interest lies in the estimation property of unconditional expected returns and the covariance matrix.

- we project the time-varying coefficients of each asset onto its fundamental characteristics
- the conditional expected returns and covariance matrix are driven by macro predictors and fundamental characteristics
- we can study factor rotation under changing macroeconomic conditions over time and maintain the heterogeneity of assets


Particular attention should be paid to modeling multiple assets. In this case, the time series of asset return is usually short (e.g., monthly data with hundreds of observations), but the number of time series is relatively large (e.g., hundreds or even thousands of assets). Researchers either sacrifice the potential benefit from massive data and model each asset independently (time series modeling) or ignore the heterogeneity of assets, stack all time-series together, and train a single model (pool modeling).3 Neither way properly takes advantage of information from massive data. Time series fits individual assets poorly due to the small sample size used, whereas pooled modeling is naive and loses heterogeneous signals. Stock return data usually suffer from extremely low signal-to-noise ratios, and the predictive power of predictors changes under different macroeconomic conditions. Therefore, it is desirable to model returns jointly while assuming the heterogeneity of individual assets.


The Markov chain Monte Carlo (MCMC) sampling process


