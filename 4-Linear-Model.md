> Linear Models

It is difficult to determine a minimum variance unbiased (MVU) estimator in general. If the signal model is a linear model, a MVU can be easily found.

# Summary

- The MVU estimator for the linear model is efficient.

# Definition of Linear Models

The linear model is defined as

$$x[n]=A+Bn+w[n],\quad n=0,1,\cdots,N-1,$$

where $w[n]$ is additive white Gaussian noise (AWGN), and the slope

---

**Theorem: Minimum Variance Unbiased Estimator for the Linear Model.** If the data observed can be modeled as

$$\mathbf{x=H\theta+w},$$

where $\mathbf{x}$ is an $N\times1$ vector of observations, $\mathbf{x}$ is a known $N\times p$ observation matrix (with $N>p$) and rank $p$, $\boldsymbol{\theta}$ is a $p\times1$ vector of parameters to be estimated, and $\mathbf{w}$ is an $N\times1$ noise vector with PDF $\mathcal{N}(\mathbf{0},\sigma^2\mathbf{I})$, then the MVU estimator is

$$\hat{\boldsymbol{\theta}}=\left(\mathbf{H}^T\mathbf{H}\right)^{-1}\mathbf{H}^T\mathbf{x},$$

and the covariance matrix of $\hat{\boldsymbol{\theta}}$ is

$$\mathbf{C}_{\hat{\boldsymbol{\theta}}}=\sigma^2\left(\mathbf{H}^T\mathbf{H}\right)^{-1}.$$

**For the linear model the MVU estimator is efficient in that it attains the CRLB.**

---