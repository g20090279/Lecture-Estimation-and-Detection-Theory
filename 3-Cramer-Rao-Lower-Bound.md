> Cramer-Rao Lower Bound

The Cramer-Rao lower bound (CRLB) is a lower bound on the **variance** of **any unbiased** estimator. It is independent of any specific estimator. For a biased estimator, its variance may be lower than the CRLB.

# 1. Introduction

## 1.1. Estimator Accuracy Considerations

Since all our information is embodied in the observed data and the underlying PDF for that data, it is not surprising that the estimation accuracy depends directly on the PDF. For instance, we should not expect to be able to estimate a parameter with any degree of accuracy if the PDF depends only weakly upon that parameter, or in the extreme case, if the PDF does not depend on it at all. **In general, the more the PDF is influenced by the unknown parameter, the better we should be able to estimate it**.

## 1.2. Summary

- CRLB is the **smallest variance** for **all unbiased** estimators.
- Many other variance bounds exist, among which CRLB is the easiest to calculate.
- The relation between CRLB and MVU estimator:
  - an unbiased estimator attains CRLB => a MVU estimator;
  - CRLB not attains =/=> a MVU estimator may or may not exist;
  - CRLB may or may not exist <=/= a MVU estimator
  
  $-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]$ may not be written in a close form, e.g., needs some relaxation. The bound is therefore not attained, which means that an unbiased estimator that attains the CRLB does not exist. However, a MVU estimator may exist. (From CRLB, we don't know how to determine whether an MVU esitmator exists, and if it does, how to find it. We can answer these questions with the theory of **sufficient statistics**.)
- If the **equality constraints** of the CRLB theorem are **satisfied** (check the derivation), it is possible to determine the MVU estimator from CRLB.
- An estimator which is unbiased and attains the CRLB is said to be ***efficient*** in that it **efficiently uses the data** (Kay 2009, §3.4, P34).
- Intuitively, the **more information**, the **lower the bound**. For independent observation, $\ln p(\mathbf{x};\theta)=\sum_{n=0}^{N-1}\ln p(x[n];\theta)$, the Fisher information is
$I(\theta)=-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]=-\sum_{n=0}^{N-1}\mathbb{E}\left[\frac{\partial^2\ln p(x[n];\theta)}{\partial\theta^2}\right]=Ni(\theta).$ For completely dependent samples, e.g., only $x[0]$ is a random variable while the other samples are $x[0]=x[1]=\cdots=x[N-1]$, we have $I(\theta)=i(\theta)$ due to $p(x[n];\theta)=1$ for $n>0$.
- For estimating a function of parameter, the **efficiency** of an estimator is **maintained** of a **linear (actually affine) transformation** while is **destoryed** by a **nonlinear transformation**.


# 2. CRLB - Scalar Parameter

## 2.1. CRLB and Its Regulartiy Condition

We are going to estimate a parameter $\theta$. We have a sequence of observation $\mathbf{x}$ which have the PDF $p(\mathbf{x};\theta)$. If the PDF is viewed as a function of the unknown parameter (with $\mathbf{x}$ fixed), it is termed the ***likelihood function***. Intuitively, the "sharpness" of the likelihood function determines how accurately we can estimate the unknown parameter, which is effectively measured by the **negative of the second derivative** (*curvature* of the log-likelihood function) of the logarithm of the likelihood function at its peak.

The variance of any unbiased estimator $\hat{\theta}$ must satify (derivation in [Appendix A](#appendix))

$$\mathrm{var}\left(\hat{\theta}\right)\geq\frac{1}{-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]},$$

if the PDF $p(\mathbf{x};\theta)$ satisfies the *"regularity"* condition (limit the usage of CRLB - only in the exponential function family)

$$\mathbb{E}\left[\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right]=0,\quad \forall\theta.$$

The derivaive is evaluated at the true value of $\theta$, and the expectation is taken with respect to $p(\mathbf{x};\theta)$:

$$\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]=\int\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}p(\mathbf{x};\theta)\ d\mathbf{x}.$$

---

**Example**: the regularity condition doesn't hold

If $x[n]$ for $n=0,1,\cdots,N-1$ are IID accroding to $\mathcal{U}[0,\theta]$, show that the regularity condition does not hold or that

$$\mathbb{E}\left[\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right]\neq0,\quad \forall\theta>0.$$

Hence, the CRLB cannot be applied to this problem.

**Solution**: 

The PDF is

$$p(\mathbf{x};\theta)=\prod_{n=0}^{N-1}\frac{1}{\theta}=\frac{1}{\theta^{N}},\quad0\leq x[0],x[1],\cdots,x[N-1]\leq\theta.$$

The logirthm of the PDF is

$$\ln p(\mathbf{x};\theta)=-N\ln\theta.$$

The regularity condition is

$$\mathbb{E}\left[\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right]=\mathbb{E}\left[-\frac{N}{\theta}\right]=\int-\frac{N}{\theta}p(\mathbf{x};\theta)\ d\mathbf{x}=-\frac{N}{\theta}\neq0,$$

indicating the regularity condition is **violated**. The problem is solved.

We can also get the same result from the chain rule

$$\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}=\frac{1}{p(\mathbf{x};\theta)}\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}=\theta^{N}\frac{-(N)}{\theta^{N+1}}=-\frac{N}{\theta}.$$

We can have a deeper look in this problem. We can see that the violation is due to

$$\int\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\ d\mathbf{x}=\int\frac{-N}{\theta^{N+1}}\ d\mathbf{x}=-\frac{N}{\theta^{N+1}}\theta^N=-\frac{N}{\theta},$$

or more specifically

$$\int\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\ d\mathbf{x}\neq\frac{1}{\partial\theta}\int p(\mathbf{x};\theta)\ d\mathbf{x}=0,$$

which is assumed to hold in the derivation of scalar parameter CRLB.

> This means that CRLB is only valid (the regularity condition is satisfied) if the the **order** of **differentiation** and **integration** may be **interchanged**. This is generally true except when the **domain** of the PDF for which it is nonzero **depends on** the **unknown parameter** such as in this example problem.

---

## 2.2. From CRLB to MVU estimator

We can use CRLB to derive a minimum variance unbiased (MVU) estimator. This MVU estimator may be found if and only if we can write in this form

$$\frac{\partial\ln p(\mathbf{x};\theta)}{\partial \theta}=I(\theta)\left(g(\mathbf{x})-\theta\right),$$

for some functions $g$ and $I$. And the **MVU estimator** is 

$$\hat{\theta}=g(\mathbf{x}),$$

and the minimum variance is

$$\frac{1}{I(\theta)}.$$

> If an estimator meets CRLB, it is MVU estimator. However, it is not true on the opposite side, i.e. if an estimator is a MVU estimator, it may not have the CRLB (e.g. the regularity condition doen't hold).

## 2.3. Fisher Information

The Fisher information for the data $\mathbf{x}$ is defined as the denominator of the CRLB

$$I(\theta)=-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right].$$

# 3. Transformation of Parameters

# 4. CRLB - Vector Parameter

# 5. Appendix

## 5.1. A: Derivation of Scalar Parameter CRLB

In this appendex we derive the CRLB for a scalar parameter $\alpha$ which is **a function of another parameter** $\alpha=g(\theta)$ where the PDF is parameterized by $\theta$. For an unbiased estimator $\hat{\alpha}$ we have

$$\mathbb{E}[\hat{\alpha}]=\int\hat{\alpha}p(\mathbf{x};\theta)\ d\mathbf{x}=\alpha=g(\theta).$$

Before begining the derivation we first examine the regulartiy condition

$$\mathbb{E}\left[\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right]=0,$$

which is assume to hold. This condition will be satisfied if the order of differentiation and integration may be interchanged, since we can rewrite the regularity condition as

$$\int\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}p(\mathbf{x};\theta)\ d\mathbf{x}=\int\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\ d\mathbf{x}=\frac{\partial}{\partial\theta}\int p(\mathbf{x};\theta)\ d\mathbf{x}=\frac{\partial1}{\partial\theta}=0.$$

The important assumption is then $\int\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\ d\mathbf{x}=\frac{\partial}{\partial\theta}\int p(\mathbf{x};\theta)\ d\mathbf{x}$.

This is **generally true except** when the **domain of the PDF** for which it is nonzero **depends on** the **unkown parameter**.

Differentiating both sides of the first equation, we have (estimator $\hat{\alpha}$ is a function of observation $\mathbf{x}$)

$$\int\hat{\alpha}\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\ d\mathbf{x}=\frac{\partial g(\theta)}{\partial\theta}.$$

The above equation can also be written as

$$\int\hat{\alpha}\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}p(\mathbf{x};\theta)\ d\mathbf{x}=\frac{\partial g(\theta)}{\partial\theta}.$$

**Combine the regularity condition** to produce

$$\int\left(\hat{\alpha}-\alpha\right)\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}p(\mathbf{x};\theta)\ d\mathbf{x}=\frac{\partial g(\theta)}{\partial\theta}.$$

By applying the Cauchy-Schwarz inequality

$$\left[\int w(\mathbf{x})g(\mathbf{x})h(\mathbf{x})\ d\mathbf{x}\right]^2\leq\int w(\mathbf{x})g^2(\mathbf{x})\ d\mathbf{x}\int w(\mathbf{x})h^2(\mathbf{x})\ d\mathbf{x}$$

which holds with equality if and only if $g(\mathbf{x})=ch(\mathbf{x})$ for $c$ some constant not dependent on $\mathbf{x}$, where

$$\begin{aligned}
    w(\mathbf{x})&=p(\mathbf{x};\theta)\\
    g(\mathbf{x})&=\hat{\alpha}-\alpha\\
    h(\mathbf{x})&=\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta},
\end{aligned}$$

we have 

$$\left(\frac{\partial g(\theta)}{\partial\theta}\right)^2\leq\int\left(\hat{\alpha}-\alpha\right)^2p(\mathbf{x};\theta)d\mathbf{x}\int\left(\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right)^2p(\mathbf{x};\theta)d\mathbf{x}$$

or the **CRLB of a function of a parameter**, i.e. $\alpha=g(\theta)$:

$$\boxed{\mathrm{var}\left(\hat{\alpha}\right)\geq\frac{\left(\frac{\partial g(\theta)}{\partial\theta}\right)^2}{\mathbb{E}\left[\left(\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right)^2\right]}=\frac{\left(\frac{\partial g(\theta)}{\partial\theta}\right)^2}{-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]}}.$$

Note the following equality

$$\mathbb{E}\left[\left(\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right)^2\right]=-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right].$$

We can prove the above equation. Calculate the second order derivative

$$\begin{aligned}
    \frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}&=\frac{\partial}{\partial\theta}\left[\frac{1}{p(\mathbf{x};\theta)}\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\right]\\
    &=-\frac{1}{\left[p(\mathbf{x};\theta)\right]^2}\left[\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\right]^2+\frac{1}{p(\mathbf{x};\theta)}\frac{\partial^2p(\mathbf{x};\theta)}{\partial\theta^2}
\end{aligned}$$

then the expectation is

$$-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]=\mathbb{E}\left[\frac{1}{\left[p(\mathbf{x};\theta)\right]^2}\left[\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}\right]^2\right]-\mathbb{E}\left[\frac{1}{p(\mathbf{x};\theta)}\frac{\partial^2p(\mathbf{x};\theta)}{\partial\theta^2}\right].$$

With the regularity condition, the second term of the expectation

$$\begin{aligned}
    \mathbb{E}\left[\frac{1}{p(\mathbf{x};\theta)}\frac{\partial^2p(\mathbf{x};\theta)}{\partial\theta^2}\right]&=\int\frac{\partial^2p(\mathbf{x};\theta)}{\partial\theta^2}d\mathbf{x}\\
    &=\frac{\partial}{\partial\theta}\int\frac{\partial p(\mathbf{x};\theta)}{\partial\theta}d\mathbf{x}\\
    &=\frac{\partial}{\partial\theta}\mathbb{E}\left[\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}\right]=0
\end{aligned}$$

If $\alpha=g(\theta)=\theta$, we have the **CRLB for scalar parameter**

$$\boxed{\mathrm{var}\left(\hat{\alpha}\right)\geq\frac{1}{-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]}}.$$

Note that the condition for equality is

$$\boxed{\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}=\frac{1}{c}\left(\hat{\alpha}-\alpha\right)},$$

where $c$ can depend on $\theta$ but not on $\mathbf{x}$. If $\alpha=g(\theta)=\theta$, we have

$$\frac{\partial\ln p(\mathbf{x};\theta)}{\partial\theta}=\frac{1}{c(\theta)}\left(\hat{\alpha}-\alpha\right).$$

The possible dependence of $c$ on $\theta$ is noted. To determine $c(\theta)$, take the expectation on the both side

$$\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}=-\frac{1}{c(\theta)}+\frac{\partial\left(\frac{1}{c(\theta)}\right)}{\partial\theta}\left(\hat{\theta}-\theta\right)$$

resulting in

$$-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]=\frac{1}{c(\theta)}$$

due to $\mathbb{E}\left[\hat{\theta}\right]=\theta$.

And finally

$$c(\theta)=\frac{1}{-\mathbb{E}\left[\frac{\partial^2\ln p(\mathbf{x};\theta)}{\partial\theta^2}\right]}=\frac{1}{I(\theta)}.$$

Therefore, we can use **the condition for equality** (the above boxed equation) to **find** an unbiased estimator that attains the CRLB (MVU estimator).