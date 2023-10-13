Recall that:
> [!tip] Confidence bounds for variance
> If $s^2$ is the sample variance from a random sample of $n$ observations from a normal distribution with unknown variance $\sigma^2$, then a $100(1-\alpha)$% confidence interval on $\sigma^2$ is
> $$\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}} \leq \sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}$$
> It also holds there are one-sided confidence intervals for variance:
> $$\frac{(n-1)s^2}{\chi^2_{\alpha, n-1}} \leq \sigma^2$$
> $$\sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{1-\alpha, n-1}}$$

Generally, you will use a table to find the $\chi^2$ values, but you can also use the inverse $\chi^2$ function on your calculator if it exists. Again, note that:
- for two-sided confidence intervals, you will want to use an area of $(1-\alpha)+\frac{\alpha}{2}$ - this corresponds to the right edge of the area.
- for one-sided confidence intervals, simply use the desired area of $1-\alpha$, since these are oriented towards the infinite.

## Section 8.4
We now move onto the notion of the population and sample proportions.

The **population proportion** $p$ is the proportion of the entire population with a specified attribute.

The **sample proportion** $\hat{p}$ is the proportion of the entire population with a specified attribute.

Supposing that a random sample of size $n$ has been taken from a large population, such that $X$ observations in the sample belong to the group of interest (of course, $X \leq n$):
- then $\hat{P} = X/n$ is a point estimator of the proportion population $p$ that belongs to this class
- and $n$ and $p$ are the parameters of a binomial distribution, such that the sampling distribution of $\hat{P}$ are approximately normal with mean $p$ and variance $p(1-p)/n$, when both $np$ and $n(1-p)$ are greater than or equal to 5.

That is, 
>[!tip]
>If $X$ is the number of observations in a sample size of $n$, such that $X/n$ is an estimate of the population proportion $p$, then the distribution
>$$Z = \frac{X-np}{\sqrt{np(1-p)}} = \frac{\hat{P}-p}{\sqrt{\frac{p(1-p)}{n}}}$$
>is approximately standard normal.

We can construct a confidence interval for the population proportion $p$ from a point estimate $\hat{P}$ given that the distribution is approximately normal.

In general, it is true that
$$P(-z_{\alpha/2} \leq Z \leq z_{\alpha/2}) \approx 1-\alpha$$

for any normally distributed $Z$ and a confidence interval constructed with $\alpha$.

If we substitute for $Z$, we get
$$P\left(-z_{\alpha/2} \leq \frac{\hat{P}-p}{\sqrt{\frac{p(1-p)}{n}}} \leq z_{\alpha/2}\right) \approx 1-\alpha$$

and isolating for $p$ gives us

> [!tip] Two-sided confidence interval for population proportion
> $$P\left(\hat{p} -z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \leq p \leq \hat{p}+z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \right)\approx 1-\alpha$$

and because this is normally distributed, notice that we can use the same principle for the two-sided confidence intervals as when constructing a confidence interval for the normally distributed sampling distribution for $\bar{X}$, the sample mean.

Of course, we also have one-sided confidence intervals expressed as

> [!tip] One-sided confidence interval for population proportion
> $$\hat{p} -z_{\alpha}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \leq p$$
> and
> $$p \leq \hat{p}+z_{\alpha}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$

> [!example]
> In a random sample of 85 automobile engine crankshaft bearings, 10 have a surface finish that is rougher than the specifications allow.  Construct both a one-sided and two-sided 95% confidence interval for $p$, the proportion of bearings in the population that exceed the roughness specification.  

Notice that $\hat{p} = 0.12$, and $n=85$.

For a two-sided 95% confidence interval, $z_{\alpha/2} = 1.96$.  Applying our formulas above yield a confidence interval of 0.0509 to 0.1891, signifying that somewhere between 5% and 19% of the bearings in the population exceed the roughness specification (with 95% confidence).

Likewise, for a one-sided 95% confidence interval, $z_{\alpha} = 1.64$. We can apply the formulas above in a similar manner.

---
Again, it holds that we can express the error (in a two-sided confidence interval, since the length of a one-sided confidence interval is infinite) as

$$E=z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$
such that $2E$ is the length of the confidence interval.

Therefore, it holds that the error can be decreased by increasing $n$; in turn, it holds that the size of the interval decreases.

As with controlling the length of the confidence interval under the same confidence level for the population mean, we can do the same here.

By rearranging for $n$, we get

> [!tip] Sample size for specific error of a two-sided confidence interval for proportion, $\hat{p}$ known
$$n = \left(\frac{z_{\alpha/2}}{E}\right)^2*\hat{p} (1-\hat{p})$$

But there's a problem - we don't know what $\hat{p}$ is until we measure it, in which case $n$ is not calculable until we perform the sample. So instead, we may use a known *prior* $p$ or $\hat{p}$ for a similar population, and assume it also holds:
$$n = \left(\frac{z_{\alpha/2}}{E}\right)^2*p (1-p)$$

But an alternative method is to assume that $\hat{p}(1-\hat{p})$ is maximized, thus giving an upper bound for $n$ such that *any* $\hat{p}$ will yield a confidence interval with an error less than $E$.

We can maximize this by taking the deriviative of $\hat{p}(1-\hat{p})$ and solving for zero. This yields 0.25, such that we can use
> [!tip] Sample size for specific error of a two-sided confidence interval for proportion, $\hat{p}$ unknown
> $$n = \left(\frac{z_{\alpha/2}}{E}\right)^2*0.25$$
> such that for any $\hat{p}$, the error will always be less than $E$ for the resulting $n$.

so that *any* sample with size $n$ always yields an error smaller than $E$. 