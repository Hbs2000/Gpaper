>*We have a lot of questions to answer: First, which characteristics really provide independent information about average returns? Which are subsumed by others? Second, does each new anomaly variable also correspond to a new factor formed on those same anomalies?... Third, how many of these new factors are really important?* <br>
> <p align="right">Cochrane(2011)</p> 


# Characteristics are covariances: A unified model of risk and return
!!! + Key
    *The IPCA mapping between characteristics and loadings
    provides a formal statistical bridge between characteristics
    and expected returns, while at the same time remaining
    consistent with the equilibrium asset pricing principle that
    risk premia are solely determined by risk exposures*
## Introduction
### Importance
The greatest collective endeavor of the asset pricing field in the past 40 years is the search for an empirical explanation of why different assets earn different average returns. The answer from equilibrium theory is clear differences in expected returns reflect compensation for different degrees of risk. But the empirical answer has proven more complicated, as some of the largest differences in performance across assets continue to elude a reliable **risk-based explanation**.

### General Background
This empirical search centers around **return factor models**, and arises from the Euler equation for investment returns. With only the assumption of “no arbitrage,” a stochastic discount factor mt+1 exists and, for any excess return ri,t, satisfies the equation
$$\begin{aligned}
E_t[m_{t+1}r_{i,t+1}^e] & = 0  \\
\Leftrightarrow E_t[r_{i,t+1}^e] &= {{Cov_t(m_{t+1},r_{i,t+1}^e)} \over {Var_t(m_{t+1})}} \Big( - {{Var_t(m_{t+1})} \over {E_t[m_{t+1}]}} \Big) \tag{1}
\end{aligned}$$

The loading, $\beta_{i,t}$, is interpretable as exposure to systematic risk factors, and $ \lambda_t $ as the risk price associated with factors. More specifically, when $ m_{t+1} $ is linear in factors ft+1, this maps to a factor model for excess returns of the form:
$$
r_{i,t+1}^e = \alpha_{i,t} + \beta'_{i,t}f_{t+1} + \epsilon_{i,t+1} \tag{2}
$$
where $ E_t[\epsilon_{i,t+1}] = E_t[\epsilon_{i,t+1}f_{t+1}] = 0, E_t[f_{t+1}] = \lambda_t $, and, perhaps most importantly, $ \alpha_{i,t}=0 $ for all $i$ and $t$. The factor
framework in (2) that follows from the asset pricing Euler equation (1) is the setting for most empirical analysis of expected returns across assets.

### General Problem
There are many obstacles to empirically analyzing Eqs. (1) and (2), the most important being that the factors and loadings are unobservable.2 

### From general to specific
There are two common approaches that researchers take.

* The first pre-specifies factors as **sorted portfolios based on previously established knowledge** about the empirical behavior of average returns, **treats these factors as fully observable** by the econometrician, and then estimates betas and alphas via regression. This approach is exemplified by
Fama and French (1993). A shortcoming of this approach is that it requires previous understanding of the cross section of average returns. But this is likely to be a partial understanding at best, and at worst is exactly the object of empirical interest.
* The second approach is to **treat risk factors as latent and use factor analytic techniques**, such as principal components analysis (PCA), to simultaneously estimate the factors and betas from the panel of realized returns, a tactic pioneered by Chamberlain and Rothschild (1983) and Connor and Korajczyk (1986). This method uses a purely statistical criterion to derive factors, and has the advantage of requiring no ex ante knowledge of the structure of average returns. A shortcoming of this approach is that PCA isill-suited for estimating conditional versions of Eq. (2) because it can only accommodate static loadings. Furthermore, PCA lacks the flexibility for a researcher to incorporate other data beyond returns to help identify a successful asset pricing model.

### Literature review
A standard protocol has emerged in the literature: When researchers propose a new characteristic that aligns
with future asset returns, they build portfolios that exploit the characteristic’s predictive power and test the alphas of these portfolios relative to some previously established pricing factors such as those from Fama and French(1993, 2015).

### Gap
This protocol is unsatisfactory as it **fails to fully account for the gamut of proposed characteristics in prior literature**. 

### The Paper Itself
#### Purpose or Focus
Our method offers a different protocol that treats the multivariate nature of the problem. When a new anomaly characteristic is proposed, it can be included in an IPCA specification that also includes the long list of characteristics from past studies. Then, IPCA can estimate the proposed characteristic’s marginal contribution to the model’s factor loadings and, if need be, its anomaly intercepts, after controlling for other characteristics in a complete multivariate analysis.
#### Motivation
Our central motivation in developing IPCA is to build a model and estimator that admits the **possibility** that characteristics line up with average returns because they proxy for loadings on common risk factors.

Indeed, if the “characteristics/expected return” relationship is driven by compensation for exposure to latent risk factors, IPCA will identify the corresponding latent factors and betas. But, if no such factors exist, the characteristic effect will be ascribed to an intercept. This immediately yields an **intuitive intercept test** that discriminates whether a characteristic-based return phenomenon is consistent with a beta/expected return model, or if it is compensation without risk (a so-called “anomaly”).

Rather than asking the GRS question “***do some pre-specified factors explain the anomaly***?,” our IPCA test asks “***does there exist some set of common latent risk factors that explain the anomaly***?”

#### ==Innovation==
* Differentiate whether a characteristic is better interpreted as a proxy for systematic risk exposure or as an anomaly alpha.
* Assess the incremental explanatory power of an individual characteristic against a (potentially high dimension) set of competing characteristics.
* Compare latent factors against pre-specified alternative factors. The results of these tests conclude that stock characteristics are best interpreted as risk loadings, that most of the characteristics proposed in the literature contain no incremental explanatory power for returns, and that commonly studied pre-specified factors are inefficient in a mean-variance sense.


### Findings
Our analysis judges asset pricing models on two criteria.

First, a successful factor model should **excel in describing the common variation in realized returns**. That is, it should accurately describe systematic risks.

We measure this according to a factor model’s total panel $R^2$. We define total $R^2$ as the fraction of variance in $R_{i,t+1}$ described by $\hat{β}'_{i,t} \hat{f}_{t+1}$, where $\hat{β}'_{i,t}$ are **estimated dynamic loadings** and $\hat{f}_{t+1}$ are the model’s **estimated common risk factors**. The total $R^2$ thus includes the explained variation due to **contemporaneous** factor realizations and dynamic factor exposures, aggregated over all assets and time periods.

Second, a successful asset pricing model should **describe differences in average returns across assets**. That is, it should accurately describe risk compensation. 

To assess this, we define a model’s predictive $R^2$ as the explained variation in $r_{i,t+1}$ due to $\hat{β}'_{i,t}\lambda_t$ (which is the model-based conditional expected return on asset i given t information), where $\lambda_t$ is the vector of estimated factor risk prices. The predictive R2 measures the accuracy of model-implied conditional expected returns

### Related Approach

(1) One branch of this literature analyzes **latent factor models for returns**
* Beginning with Ross (1976) seminal Arbitrage Pricing Theory (APT). Empirical contributions to this literature, such as Chamberlain and Rothschild (1983) and Connor and Korajczyk (1986, 1988), rely on principal component analysis of returns. 
* Our primary innovation relative to this literature is to bring **the wealth of characteristic information** into latent factor models and, in doing so, make it possible to tractably analyze latent factor models with dynamic loadings.

(2) Another strand of literature models **factor loadings as functions of observables**.
*  Most closely related are models in which factor exposures are functions of firm haracteristics, dating at least to Rosenberg (1974). In contrast to our contributions, Rosenberg’s analysis is primarily theoretical, assumes that factors are observable, and does not provide a testing framework. Ferson and Harvey (1999) allow for dynamic betas as asset-specific functions of macroeconomic variables. They differ from our analysis by relying on observable factors and focusing on macro rather than firm-specific instrumental variables. Daniel and Titman (1997) directly compare stock characteristics to factor loadings in terms of their ability to explain differences in average returns, an approach recently extended by Chordia et al. (2015).
* IPCA is unique in nesting competing characteristic and beta models of returns while simultaneously estimating the latent factors that most accurately coincide with characteristics as loadings, rather than relying on pre-specified factors.

(3) Third literature models **stock returns as a function of many characteristics** at once.  
* This literature has emerged only recently in response to an accumulation of research on predictive stock characteristics, and exploits more recently developed statistical techniques for high dimensional predictive systems.
* Lewellen (2015) analyzes the joint predictive power of up to 15 characteristics in ordinary least squares regression. Light et al. (2017) and Freyberger et al. (2017) consider larger collections of predictors than Lewellen and address concomitant statistical challenges using partial least squares and LASSO, respectively, while Gu et al. (2018) compare a gamut of machine learning methods for predicting returns with nearly a thousand firm characteristics. These papers **take a pure return forecasting approach and do not attempt to develop an asset pricing model or conduct asset pricing tests**.

Kozak et al. (2018, 2019) show that a small number
of principal components from 15 anomaly portfolios (from
Novy-Marx and Velikov, 2016) are able to price those same
portfolios with insignificant alphas. 

Our results illustrate that while that model works well for pricing their specific anomaly portfolios, the same model (and the PCA approach more generally) **fails with other sets of test assets**.

IPCA reconciles this inconsistency by allowing assets’ loadings to transition smoothly as characteristics evolve. As a result, IPCA successfully prices **individual stocks as well as anomaly or other stock portfolios**.

# Shrinking the cross section
## Introduction
### Importance
The empirical asset pricing literature has found a large number of stock characteristics that help predict cross-sectional variation in expected stock returns.

### General Background
Researchers have tried to summarize this variation with factor models that include a small number of characteristics-based factors. That is, they seek to find a **characteristics-sparse stochastic discount factor (SDF) representation** that is linear in only a few such factors.

### Genaral Problem
Unfortunately, it seems that as new cross-sectional predictors emerge, these factor models need to be **modified and expanded** to capture the new evidence: Fama and French (1993) proposed a three factor model, Hou et al. (2015) have moved on to four, Fama and French (2015) to five factors, and Barillas and Shanken (2018) argue for a six-factor model.

Even so, research in this area has tested these factor models only on portfolios constructed from a relatively small subset of known cross-sectional return predictors. 

These papers do not tell us how well characteristics-sparse factor models would do if one **confronted them with a much larger set of cross-sectional return predictors** and an examination of this question is statistically challenging due to **the high-dimensional nature of the problem**.

### From General to Specific
If it were possible to characterize the cross-section in terms of a few characteristics, this would imply **extreme redundancy** among the many dozens of known anomalies.

### Literature Review
However, upon closer examination, models based on present-value identities or q-theory that researchers have used to interpret the relationship between characteristics and expected returns do not really support the idea that only a few stock characteristics should matter. For example, a present-value identity can motivate why the book-to-market ratio and expected profitability could jointly explain expected returns. Expected profitability is not directly observable, though. A large number of observable stock characteristics could potentially be
useful for predicting cross-sectional variation in future profitability—and therefore also for predicting returns.


### Gap
The conventional approach would be to estimate SDF coefficients with a cross-sectional regression of average returns on covariances of returns and factors. Due to the large number of potential factors, this conventional approach would lead to **spurious overfitting**.

### The Paper Itself
#### Purpose or Focus
To overcome this high-dimensionality challenge, we use a Bayesian approach with **a novel specification of prior beliefs**.

Asset pricing models of various kinds generally imply that much of the variance of the SDF should be attributable to higheigenvalue (i.e.,high-variance) principal components (PCs) of the candidate factor returns. ***Put differently, first and second moments of returns should be related.***

Therefore, if a factor earns high expected returns, it must either itself be a major source of variance or load heavily on factors that are major sources of variance.

#### Methodology

We construct a prior distribution that reflects these economic considerations. Compared to the naïve ordinary least squares (OLS) estimator, **the Bayesian posterior shrinks the SDF coefficients toward zero**. Our prior specification shares similarities with the prior in Pástor (2000) and Pástor and Stambaugh (2000). Crucially, however, **the degree of shrinkage in our case is not equal for all assets**. Instead, the posterior applies significantly **more shrinkage to SDF coefficients associated with *low-eigenvalue PCs***. This heterogeneity in shrinkage is consistent with our economic motivation for the prior, and it is empirically important, as it leads to better out-of-sample (OOS) performance.

Our Bayesian estimator is similar to ridge regression—a popular technique in machine learning—but with important differences. The ridge version of the regression of average returns on factor covariances would add a **penalty on the sum of squared SDF coefficients (L2 norm)** to the least-squares objective. In contrast, our estimator imposes a penalty based on the maximum squared Sharpe ratio implied by the SDF—in line with our economic motivation that near-arbitrage opportunities are implausible and likely spurious. This estimator is in turn equivalent to one that **minimizes the Hansen and Jagannathan (1997) distance** and imposes a penalty on the sum of squared SDF coefficients (L2 norm). Our baseline Bayesian approach results in shrinkage

### Further Discussion
Our baseline Bayesian approach results in shrinkage of many SDF coefficients to ***nearly, but not exactly, zero***. Thus, while the resulting SDF may put low weight on the contribution of many characteristics-based factors, it will not be sparse in terms of characteristics.

However, we also want to entertain the **possibility** that the weight of some of these candidate factors could truly be zero.

***First***, a substantial existing literature focuses on SDFs with just a few characteristics-based factors. While we have argued above that the economic case for this extreme degree of haracteristics-sparsity is weak, we still want to entertain it as an **empirical hypothesis**. 

***Second***, we may want to include among the set of candidate factors ones that have not been previously analyzed in empirical studies and that may therefore be more likely to have a zero risk price. For these reasons, we extend our Bayesian method to allow for automatic factor selection, that is, finding a good sparse SDF approximation.





# Taming the factor zoo
# RP-PCA

