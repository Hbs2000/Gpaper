# R Square

## Intercept or Not

> *Sometimes removal of intercept will lead to a great increase in interms of R square, why is that?*

Recall that the usual computation of $R^2$ when an intercept is included is:

$$
R^2=\dfrac{\sum_i(\hat y_i-\bar y)^2}{\sum_i(y_i-\bar y)^2}=1-\dfrac{\sum_i(y_i-\hat y_i)^2}{\sum_i(y_i-\bar y)^2}.
$$

The first equality **only** occurs because of the inclusion of the intercept even though this is probably the more popular way of writing it. 

The **second** equality actually provides *the more general interpretation*.

For the second form, it means that we compute the mean-squared error, divide it by the variance of the original observations and then subtract this from one. 



#### What happens if there is no intercept in the model? <!-- {docsify-ignore} -->

In that case, the expression turns out to be:

$$
R_0^2=\dfrac{\sum_i\hat y_i^2}{\sum_i y_i^2}=1-\dfrac{\sum_i(y_i-\hat y_i)^2}{\sum_i y_i^2}
$$

- In the former case (with intercept), $R^2$ is comparing your current model to *the reference model that only includes an intercept*.

- In the second case, there is no intercept, so it makes little sense to compare it to such a model. So, instead, $R_0^2$ is computed, which implicitly uses a reference model *corresponding to noise only*.

> [!NOTE]
> If your predictions are really bad, this value can go *negative*.


#### How and when are they different? <!-- {docsify-ignore} -->




## Centered and Uncertained









