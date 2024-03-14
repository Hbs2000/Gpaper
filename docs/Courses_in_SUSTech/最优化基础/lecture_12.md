# Foundations of optimization 12

## Nonlinear Extension of LP

$\geq$ is a **partial order** on $\mathbb{R}^n$ because it satisfies a-e.

a. Reflexivity: $u \geq u$ for all $u \in \mathbb{R}^n$

b. Anti-Symmetry: $u \geq v$ and $v \geq u$ imply $u=v$

c. Transitivity: $u \geq v$ and $v \geq w$ imply $u \geq w$

d. Homogeneity: for any $u,v \in \mathbb{R}^n$, $\alpha \geq 0$, if $u \geq v$, then $\alpha u \geq \alpha v$

e. Additivity: for any $u,v,w,z \in \mathbb{R}^n$, if $u \geq v$ and $w \geq z$, then $u + w \geq v + z$

现在我们定义一种新的 relation。

Let $E$ be a finite-dimensional Euclidean space equipped with an inner product $\bullet$ and a relation $\succeq$

We say a relation $\succeq$ is **good** if it satisfies a-e.

> [!TIP|label:Pointed cone]
> the set $K = \{ u \in E: u \succeq 0 \}$ is a **pointed cone**
> 
> 1. $K$ is non-empty and closed under addition: $u+v \ in K$ whenever $u,v \in K$
> 2. $K$ is a cone: for any $u \in K$ and $\alpha > 0$, we have $\alpha u \in K$
> 3. $K$ is pointed: if $u,-u \in K$, then $u=0$

Given an arbitrary pointed cone, the relation 

$$
u\succeq_Kv\Longleftrightarrow u-v\in K
$$

is also a good relation.


## Examples of Pointed Cone

We define **Non-Negative Orthant** 【非负象限锥】: 

$$
\mathbb{R}_+^n=\{(x_1,...,x_n)\in\mathbb{R}^n:x_i\geq0\mathrm{~for~}i=1,...,n\}
$$

We consider $\mathbb{R}_+^n$ as a pointed cone in $\mathbb{R}^n$ equipped with the usual inner product $u\bullet v=\sum_{i=1}^nu_iv_i$

**Lorentz Cone** (Second-Order Cone)【二阶锥，也可泛化为 $p$ 阶锥】

$$
\mathcal{Q}^{n+1}=\{(t,x)\in\mathbb{R}\times\mathbb{R}^n:t\geq||x||_2\}
$$

We consider $\mathcal{Q}^{n+1}$ as a pointed cone in $\mathbb{R}^{n+1}$ equipped with the usual inner product.


**Positive Semidefinite Cone**【半正定矩阵锥，包含所有的 $n$ 阶半正定矩阵】

$$
S_+^n=\{X\in S^n:u^TXu\geq0\mathrm{~for~all~}u\in\mathbb{R}^n\}
$$

We consider $S_+^n$ as a pointed cone in the space $\mathcal{S}^n$ of $n \times n$ symmetric matrices equipped with Frobenius inner product

$$
X\bullet Y=tr(X^TY)=tr(XY)=\sum_{i=1}^n\sum_{j=1}^nX_{ij}Y_{ij}
$$
