Concluding our approach to hypothesis testing, we have the P-value.

The P-value is the probability that the test statistic will take on a value that is at least as extreme as the observed value of the statistic (in our case, $\bar{x}$ from our sample) when the null hypothesis $H_0$ is true.

For example, in this right-tailed test:
![[Nov 14 (test 3 review) 2022-11-14 13.09.52.excalidraw]]

Then the p-value is simply $z_0 = \frac{\bar{x} - \mu}{\sigma/\sqrt{n}}$, which is the standardization of $\bar{x}$.

In the event you have a two-tailed test, you can simply find the p-value for one side, and then multiply that by two.

In the event you have a left-tailed test, you must find the area to the left of the observed value. In summary:
- Two tailed test:
	- $H_0 = \mu = \mu_0$
	- $H_1 = \mu \neq \mu_0$
- Right=tailed test
	- $H_0 = \mu = \mu_0$
	- $H_1 = \mu \gt \mu_0$
- Left-tailed test
	- $H_0 = \mu = \mu_0$
	- $H_1 = \mu \lt \mu_0$

Recall our two-sided hypothesis for burning rate:
- $H_0 = \mu = 50$
- $H_1 = \mu \neq 50$

for which $n = 16$ and $\sigma =  2.5$. Suppose that the observed sample mean is 51.3 centimeters per second.

First, we standardize to find its z-score; $z_0 = \frac{\bar{x} - \mu}{\sigma/\sqrt{n}} = 2.08$. To find its p-value, we can simply take the CDF up to $z = -2.08$ and multiply by 2. 

---

> [!example]
> For the hypothesis test $H_0: \mu = 8$ against $H_1: \mu \lt 8$ and variance known, calculate the P-value when the test statistic $z_0 = -1.84$.

Since this is a left-tailed test (that is, our extremes are considered to be in the left tail). Therefore, it is sufficient to simply find the CDF up to -1.84.

## General procedure for hypothesis test
- **Parameter of interest:** From the problem context, identify the parameter of interest. In our case, this will be the mean or the proportion.
- **Null hypothesis:** State the null hypothesis, $H_0$, which is always expressed as an equality.
- **Alternative hypothesis:** Specify an appropriate alternative - expressed as one of $\neq, \lt, \gt$ - as $H_1$.
- **Test statistic:** Determine an appropriate test statistic. In our case, we generally use $\bar{x}$, the sample mean. Additionally, determine its z-score.
- Specify the location of the critical region (two-tailed, upper-tailed, or lower-tailed), as well as the criteria for rejection (the value of $\alpha$ or the P-value for which rejection occurs).
- **RESOLVE**

---

You probably want to copy the critical values $z_{\alpha}$ for one- and two-sided confidence interval, instead of memorizing them or using `invNorm()`.

Table 4 will be provided, but you should also verify that a given $\chi^2_{\alpha, df}$ gives what you expect.

You should know:
- how to find sample standard deviation and variance *manually*
- frequency distribution construction (you'll be given the bin count and starting values)
- how to apply the central limit theorem - namely, that the sampling mean distribution is normal if the population itself is normally distributed, and that this gives you z-scores that you can use
- construction of confidence intervals (both two-sided and one-side) for the population mean, derived from the sample mean, using the full formula - involves normal distribution and critical values from the normal distribution
- finding the desired sample size from a desired confidence level and interval length (or error, which is half the length)
- construction of confidence intervals for the population variance, using the full formula - involves the $\chi^2$ distribution and critical values from $\chi^2$
- construction of confidence intervals for the population proportion, using the full formula - involves the normal distribution
- finding basic statistics, like the point estimate $\hat{p} = X/n$