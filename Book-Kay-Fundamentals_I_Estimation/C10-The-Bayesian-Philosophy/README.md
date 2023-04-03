- Key Words: The Bayesian Philosophy - Estimating A Random Parameter
- Last revised: Apr. 3, 2023

---

# From Classical Approach to Bayesian Approach

The classical approach to statistical estimation is for that with *deterministic* but *unknown* constant. It implies that the parameter is not a random variable. In this case, we have *two* natural metrics (refer to Chapter 2) to identify how good is an estimator: the biasness between the expectation of the estimated parameter and the true parameter, and the variance of the estimator. Note that the estimator is a random variable. These two metrics are based on the fact that the true parameter is fixed, i.e. deterministic. In many cases, we prefer to have a *minimum variance unbiased (MVU)* estimator. An unbiased estimator guarantees its means equal to exactly the true parameter, while the variance illustrates how precisely can the estimator perform. Practically, the unbiasness is the most important property, since it is not meaningful if the estimator mean can not attain the true parameter value no matter how precise is the estimated value. Note that there is another natural criterion, mean square error (MSE). However, this criterion leads to unrealizable estimator (which is the estimator that cannot be written solely as a function of data) (Section 2.4). This results from that the extra term due to bias depends on the parameter itself (Eq. (2.6)). For a unbias estimator, the MSE reduces to the variance of the estimator.

If the parameter is a random variable, the biasness property becomes vague, since the true parameter is no longer deterministic. Each observation we obtain is related to a different realization of the random variable. This is the intrinsic difference between the *normal MSE* (single integral, wrt. the observation) and the *Bayesian MSE* (double integral, one for the observation, one for the parameter). This difference can also be clarified by using a Monte Carlo simulation to access the MSE performance:

- For the classical approach, we generate many realizations of the random noise and add it to a same given parameter. (Eq. (10.3))
- For the Bayesian approach, we generate a realization of noise and a realization of parameter. The both values are different in different iterations. (Eq. (10.4))

# The Role of Prior PDF and Posterior PDF

The posterior PDF $p(A|\boldsymbol{x})$ and the prior PDF $p(A)$ of the parameter $A$ are differentiated by a reference point that if we have observed the data $\boldsymbol{x}$ or not. These two PDFs are related to each other by the Bayes' Theorem

$$p(A|\boldsymbol{x})=\frac{p(\boldsymbol{x}|A)p(A)}{p(\boldsymbol{x})}=\frac{p(\boldsymbol{x}|A)p(A)}{\int p(\boldsymbol{x}|A)p(A)dA}.$$

As a matter of fact, the conditional PDF $p(\boldsymbol{x}|A)$ is identical in form to the usual classical PDF $p(\boldsymbol{x};A)$. For the classical PDF, the semicolon means that the PDF is parametrized by the deterministic parameter $A$, while the vertical line in the condition PDF means that the parameter $A$ is a random variable but in this PDF, we assume $A$ is known.

# MMSE Estimator Is the Mean of the Posterior PDF

The *optimal estimator* in terms of minimizing the *Bayesian MSE* is the mean of he posterior PDF $p(A|\boldsymbol{x})$

$$\hat{A}=\mathbb{E}(A|\boldsymbol{x})=\int Ap(A|\boldsymbol{x})dA.$$

In many cases, we don't have the possibility to calculate the integral in a closed form, since $p(A|\boldsymbol{x})$ is usually in a complicated form.

The MMSE estimator will in general depend on the posterior PDF, i.e., the prior knowledge as well as the data. 

> If the prior knowledge is weak relative to that of the data, then the estimator will ignore the prior knowledge. Otherwise, the estimator will be "biased" towards the prior mean. As expected, the use of prior information always improves the estimation accuracy (C10.4).

The bias here is the difference between the MMSE estimator and the classical estimator. The information of prior PDF helps this process. Note that this biasness is not the same as the biasness as a metric in the classical estimation. The biasness in the classical estimation is the different between the estimator mean and the true parameter. Since the parameter is not deterministic, we cannot measure the classical biasness.

The basic principle of the MMSE is to improve the Bayesian MSE performance by allowing the estimator to be "biased".

The problem of MSE in the classical estimator, i.e. the MSE criterion leads to an unrealistic estimator, doesn't exist any more in Bayesian approach, since the Bayesian MSE considers the parameter random.