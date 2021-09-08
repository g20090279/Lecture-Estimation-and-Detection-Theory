# Minimum Variance Unbiased Estimation

There are two important metrics for an estimator: **bias** and **mean square error**. To design a estimator, we want to have an unbiased and minimum variance estimator. The unbiased constraint is desirable from a practical view point since the more natural error criterion, the **minimum mean square error**, generally leads to unrealizable estimators. **Minimum variance unbiased estimator** do not exist in general, or can not be found in general. But if they can be found, the **Cramer-Rao lower bound** and the concept of a **sufficient statistic** can help. If a minimum variance unbiased estimator does not exist, or can not be found, a further constraint, **being linear in the data**, can be applied and lead to an **easily implemented**, but **suboptimal** estimator.

## Unbiased Estimators

An estimator is said to be unbiased if the average of the estimate yiels the true value of the unknown parameter for any parameter:

$$\mathbb{E}[\hat{\theta}]=\theta,\quad a<\theta<b,$$

where $(a,b)$ denotes the range of possible values of $\theta$.

## Minimum Variance Criterion

### Minimizing MSE Leads Generally to Unrealizable Estimator 

We need to adopt some optimality criterion in order to search for optimal estimators. A natural one is the *mean square error* (MSE), defined as

$$\mathrm{mse}(\hat{\theta})=\mathbb{E}\left[\left(\hat{\theta}-\theta\right)^2\right].$$

This criterion leads to unrealizable estimators, since it is not solely a function of the data. If a estimator depends also on the parameter itself, it is **unrealizable**, as the parameter should be known first.

Although on occassion realizable minimum MSE estimators can be found, from a practical view point the minimum MSE estimator needs to be abandoned. An alternative criterion is to minimize the variance under zero-bias constraint.

To minimize the variance of an unbiased estimator, $\min\mathrm{var}[\hat{\theta}]=\min\mathbb{E}\left[\left(\hat{\theta}-\theta\right)^2\right]$, equals to minimize the MSE.

### Existance of the Minimum Variance Unbiased (MVU) Estimator

A MVU estimator is an unbiased estimator whose variance is less than that of other estimators for **all $\theta$**. This also called *uniformly minimum variance unbiased estimator*.

### Finding the Minimum Variance Unbiased Estimator

We may not be able to find the MVU estimator, even though it exists. There are several possible approaches:

1. Determine the Cramer-Rao lower bound (CRLB) and check to see if some estimator satisfies it.
2. Apply the Rao-Blackwell-Lehmann-Scheffe (RBLS) theorem.
3. Further restrict the class of estimators to be not only unbiased but also linear. Then, find the minimum variance estimator within this restricted class.

