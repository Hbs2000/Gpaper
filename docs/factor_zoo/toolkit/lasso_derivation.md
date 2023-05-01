# Lasso Derivation

Derivation of closed form lasso solution can be attacked in a number of ways, including fairly economical approaches via the Karush–Kuhn–Tucker conditions.

Below is a quite elementary alternative argument.

#### Orthonormal

$$
X^T X = I
$$

When X is composed of orthogonal columns, the ordinary least squares solution is:

$$\begin{equation}
\hat{\beta}^{OLS} = (X^T X)^{-1}X^T y = X^T y
\end{equation}$$

For the lasso problem: 

$$\begin{equation}
\underset{\beta}{min} \ {1\over2} || Y-X\beta ||_2^2 + \gamma ||\beta||_1
\end{equation}$$


Expanding out the first term we get $ {1\over2} Y^TY-Y^TX\beta + {1\over2}\beta^T X^TX \beta $, and since $Y^TY$ does not contain any of the variables of interest, we can **discard it** and consider yet another equivalent problem:

$$
\begin{equation}
\underset{\beta}{min} \ -Y^TX\beta + {1\over2}||\beta||^2+\gamma ||\beta||_1
\end{equation}
$$

Noting that $\hat{\beta}^{OLS} = X^T Y$, the previous problem can be rewritten as:

$$\begin{equation}
\underset{\beta}{min} \sum_{i=1}^p \ -\hat{\beta}_{i,OLS}\beta_i + {1\over2}\beta_i^2+\gamma |\beta_i|
\end{equation}
$$

Our objective function is now a sum of objectives, each corresponding to a separate variable $\beta_i$, so they may each be solved individually.

<hr>

<div class = 'cpart'>

The whole is equal to the sum of its parts
</div>

Fix a certain $i$. Then, we want to minimize
$$
\begin{equation}
\zeta_i = -\hat{\beta}_{i,OLS}\beta_i + {1\over2}\beta_i^2+\gamma |\beta_i|
\end{equation}
$$

If $\hat{\beta}_{i,OLS} > 0 $, then we **must have $\beta_i \geq 0$** since otherwise we could flip its sign and get a lower value for the objective function. Likewise if $\hat{\beta}_{i,OLS} < 0 $, then we must choose $\beta_i \leq 0$.

**Case 1**: $\hat{\beta}_{i,OLS} > 0 $, $\beta_i \geq 0$

Under Case 1, the objective function is:

$$
\begin{equation}
\zeta_i = -\hat{\beta}_{i,OLS}\beta_i + {1\over2}\beta_i^2+\gamma \beta_i
\end{equation}
$$

Differentiating this with respect to $\beta_i$ and setting equal to zero, we get:

$$\begin{equation}
\beta_i = \hat{\beta}_{i,OLS} - \gamma
\end{equation}$$

Since $\beta_i$ is non-negative, we have:

$$
\begin{equation}
\hat{\beta}_{i,Lasso} = (\hat{\beta}_{i,OLS}-\gamma)_+ = sgn(\hat{\beta}_{i,OLS})(|\hat{\beta}_{i,OLS}|-\gamma)_+
\end{equation}
$$

**Case 2**: $\hat{\beta}_{i,OLS} < 0 $, $\beta_i \leq 0$

Under Case 2, the objective function is:

$$
\begin{equation}
\zeta_i = -\hat{\beta}_{i,OLS}\beta_i + {1\over2}\beta_i^2-\gamma \beta_i
\end{equation}
$$

Differentiating this with respect to $\beta_i$ and setting equal to zero, we get:

$$\begin{equation}
\beta_i = \hat{\beta}_{i,OLS} - \gamma
\end{equation}$$

Again, to ensure this is feasible, $\beta_i$ should be non-positive:

$$
\begin{equation}
\hat{\beta}_{i,Lasso} = (\hat{\beta}_{i,OLS}-\gamma)_+ = sgn(\hat{\beta}_{i,OLS})(|\hat{\beta}_{i,OLS}|-\gamma)_+ = sgn(\hat{\beta}_{i,OLS})(|X_i^TY|-\gamma)_+
\end{equation}
$$

**Case 3**: $\hat{\beta}_{i,OLS} = 0 $, $\beta_i=0$, which is the minimal value of objective function and is consistent with aformentioned closed-form.

<hr>

In all those scenarios, we get the desired form.

> [!NOTE]
> As $\gamma$ increases, then each of the $|\hat{\beta}_{i,Lasso}|$ decreases, hence so does $||\hat{\beta}_{i,Lasso}||_1$.
>
> When $\gamma=0$, we recover the OLS solution, and, for $\gamma> \bm{max_i}|\hat{\beta}_{i,OLS}|$, we obtain $\hat{\beta}_{i,Lasso}=0$ for all $i$.



#### Orthogonal

$$
X^T X = D
$$

When data matrix is not orthogonal instead of orthonormal, the equation (4) turns out to be:

$$
\begin{align}
&\underset{\beta}{min} \ \hat{\beta}_{i,OLS}^T D\beta + {1\over2}\beta^T D \beta+\gamma ||\beta||_1 \\
=&\underset{\beta}{min} \sum_{i=1}^p \ -\hat{\beta}_{i,OLS}\beta_i \sigma_i^2+{\sigma_i^2\over 2}\beta_i^2 + \gamma_i
\end{align}
$$

and the whole process stays the same, and we find that:

$$
\begin{equation}
\hat{\beta}_{i,Lasso} = sgn(\hat{\beta}_{i,OLS})\left(|\hat{\beta}_{i,OLS}|-{\gamma\over \sigma_i^2}\right)_+
\end{equation}
$$

Futhermore, $ \hat{\beta}_{OLS} = D^{-1}X^TY \ \Longrightarrow \ \hat{\beta}_{i,Lasso}={X_i^T Y \over \sigma_i^2} $, so we have that:

$$
\begin{equation}
\hat{\beta}_{i,Lasso} = sgn(\hat{\beta}_{i,OLS})\left(|\hat{\beta}_{i,OLS}|-{\gamma\over \sigma_i^2}\right)_+ = {sgn(\hat{\beta}_{i,OLS})\over\sigma_i^2}\left(|X_i^T Y|-{\gamma}\right)_+
\end{equation}
$$

So there is **exactly no difference** with the Orthonomal situation in terms of **variable selection**, just but the actual coefficients $\hat{\beta}_{i,Lasso}$ are scaled according to the predictor variances.



#### Non-Diagonal

$$
X^TX = \Sigma
$$

The most stark difference between Diagonal and Non-Diagonal is that *the variables are correlated*, which means that although the variable $i$ is fixed, the effects of other predictors can not be excluded, rendering the whole aformentioned procedure paralysed. Therefore, ***we can not get a closed-form solution.***

The equation (12) turns out to be:

$$
\begin{align}
\underset{\beta}{min} \ \hat{\beta}_{i,OLS}^T \Sigma \beta + {1\over2}\beta^T \Sigma \beta+\gamma ||\beta||_1 
\end{align}
$$

$$
\begin{align}
=\underset{\beta}{min}  \left(\sum_{i=1}^p \ -\hat{\beta}_{i,OLS}\beta_i \sigma_i^2+ {\sigma_i^2\over 2}\beta_i^2 + \gamma_i\right) - \sum_{i=1,i\neq j}^p \left({1\over2}(\hat{\beta}_{i,OLS}^T\beta_j + \hat{\beta}_{j,OLS}^T\beta_j-2\beta_i \beta_j)\sigma_{i,j}\right)
\end{align}
$$






















