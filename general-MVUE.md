> General Minimum Variance Unbised Estimation

The CRLB **sometimes** results in an efficient and hence MVU estimator. If the **signal model** is **linear**, it is helpful to **easily find** the efficient estimator from CRLB.

However, is an efficient estimator does not exist, it is still of interest to be able to find the MVU estimator (assume of course that it exists). We then require the **sufficient statistics** and the important **Rao-Blackwell-Lehmann-Scheffe theorem**. With this theory, it is possible in many cases to determine the MVU estimator by a simple inspection of the PDF.

# Sufficient Statistics

The major question is: which data samples are pertinent to the estimation problem. Is there a set of data that is sufficient?

Example data sets are (they are all sufficient)

$$\begin{aligned}
    S_{1}&=\left\{x[0],x[1],\cdots,x[N-1]\right\}\\
    S_{2}&=\left\{x[0]+x[1],\cdots,x[N-1]\right\}\\
    S_{3}&=\left\{\sum_{n=0}^{N-1}x[n]\right\}.
\end{aligned}$$

- **Minimal Set**: the data set (observation) that contains the **least** number of elements.
- **Statistic**: each element in the data set (observation) can be regarded as a statistics.
- **Sufficient Statistic**: a statistic which summarizes the data in the sense that if we are given the sufficient statistic, the **PDF of the data no longer depends on the unknown parameter**. There may be multiple sufficient data sets.
- **Minimal Sufficient Statistic**: like the set $S_3$. We only need one statistic, i.e., the sum of all data samples, instead of information of every data sample, since all information has been summarized in the sufficient sstatistic.

To illustrate the term "sufficient", we consider the PDF of the data

$$p(\mathbf{x};A)=\frac{1}{(2\pi\sigma^2)^{N/2}}\exp\left[-\frac{1}{2\sigma^2}\sum_{n=0}^{N-1}\left(x[n]-A\right)^2\right]$$

# Finding Sufficient Statistics (Neyman-Fisher Factorization Theorem)

**Neyman-Fisher Factorization**: If we can factor the PDf $p(\mathbf{x};theta)$ as

$$p(\mathbf{x};\theta)=g\left(T(\mathbf{x}),\theta\right)h(\mathbf{x}),$$

where $g$ is a function dpending on $\mathbf{x}$ only through $T(\mathbf{x})$ and $h$ is a function depending only on $\mathbf{x}$, then $T(\mathbf{x})$ is a sufficient statistic for $\theta$. Conversely, if $T(\mathbf{x})$ is a sufficient statistic for $\theta$, then the PDF can be factored as the above equation.