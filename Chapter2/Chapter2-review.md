# Chapter 2 Review

## Single-parameter models 

### Estimating probability from binomial data

The sampling model follows. 

$p(y|\theta)=Bin(y|n,\theta)={n\choose y}\theta ^y (1-\theta)^{n-y}$ 

By using Bayes rule, we get

$p(\theta|y) \propto \theta ^ y (1-\theta)^ {n-y}$ 

Ultimately we have,

$\theta | y \sim Beta(y+1, n-y+1)$

*Bayes' rule was discovered independently by Bayes and Laplace independently!*

### Posterior as a compromise between data and prior information

1. The prior mean of the parameter is the average of all possible posterior means over the distribution of possible data.
2. The variance of the posterior mean of the parameter is on average, smaller that that of the prior parameter by an amount of the varaince between the posterior means. 

### Summarizing posterior inference 

1. One can report the entire posterior distribution with a visualization. 
2. When posterior distribution is in a closed form, report mean, mode, variance, etc.
3. Report posterior quantiles and intervals.
    - Central Posterior Interval.
        $100(1-\alpha)\%$
    - Highest Posterior density region.
        $100(1-\alpha)\% $ & the density within the region is always higher than that of the outside. 

### Informative prior distributions

Two interpretations can be given to prior distributions.

1. population interpretation
2. (subjective) state of knowledge interpretation. 

### Conjugacy

Posterior distribution following the same parametric form as the prior distribution. The infamous exponential family..

Say, $F$ is a class of sampling distributions $p(y | \theta)$ and $P$ is a class of prior distributions for $\theta$, then the class $P$  is conjugate for $F$ if

$$p(\theta | y ) \in P \ for \ \forall p(\cdot | \theta) \in F \ \& \  p(\cdot) \in P $$

Now for the exponential family, if all members of the class $F$ has the following form, 

$$p(y_i | \theta ) f(y_i) g(\theta) \exp(\phi(\theta)^T u(y_i))$$

where $\phi(\theta)$ and $u(y_i)$ are vectors of equal dimension to that of $\theta$, then we call this an exponential family. 

The likelihood for the sequence $y = (y_1, y_2, …)$ follows, 

$p(y \mid \theta)=\left(\prod_{i=1}^{n} f\left(y_{i}\right)\right) g(\theta)^{n} \exp \left(\phi(\theta)^{T} \sum_{i=1}^{n} u\left(y_{i}\right)\right)$ 

This can be simplified in the following form, 

$p(y \mid \theta) \propto g(\theta)^{n} e^{\phi(\theta)^{T} t(y)}, \quad$ where $t(y)=\sum_{i=1}^{n} u\left(y_{i}\right)$ 

$t(y)$ is a sufficient statistic for $\theta$, because the likelihood for $\theta$ solely depends on the data $y$ and only through $t(y)$. 

If the prior density is specified as, 

$p(\theta) \propto g(\theta)^{\eta} e^{\phi(\theta)^{T} \nu}$ 

the posterior density is as follows,

$p(\theta \mid y) \propto g(\theta)^{\eta+n} e^{\phi(\theta)^{T}(\nu+t(y))}$.

- Beta prior for Binomial Model

    - Prior
        $Beta(\theta | \alpha, \beta) \propto \theta^{\alpha -1}(1-\theta)^{\beta -1}$
    - Posterior
        $p(\theta | y,n,M) \propto \theta^y(1-\theta)^{n-y}\theta^{\alpha -1} (1-\theta)^{\beta -1}$ 
        $\sim Beta(\theta | \alpha + y, \beta + n - y)$

    $\alpha-1, \beta-1$ can be considered as number of prior observations. Note that prior is uniform on $\alpha = \beta =1$. 

    Posterior mean and variance :

    -  Mean
        $E[\theta | y] = \frac{\alpha +y}{\alpha + \beta + n}$
        as $n \to \infty, E[\theta|y] \to y/n$

    - Variance
        $Var(\theta|y) = \frac{E[\theta|y] (1-E(\theta |y))}{\alpha + \beta + n + 1}$
        as $n \to \infty, Var(\theta|y) \to 0$

    This makes perfect sense because as information(data) increases, the prior information($\alpha, \beta$) will become more and more trivial as new information is feeded to the model. 