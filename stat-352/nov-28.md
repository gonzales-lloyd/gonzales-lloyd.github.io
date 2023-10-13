**Note: this does not include the content from last Wednesday!**

## Section 9.4

Suppose our population is to instead test that the variance of a normal population $\sigma^2$ equals a specified value, say, $\sigma$, or equivalently, that the standard deviation $\sigma$ is equal to $\sigma_0$.

If $X_1, \ldots, X_n$ is a random sample of $n$ observations from this population, to test:
- $H_0: \sigma^2 = \sigma^2_0$
- $H_1: \sigma^2 \neq \sigma^2_0$

where

$$\chi^2_0 = \frac{(n-1)S^2}{\sigma^2_0}$$
then if the null hypotehsis $\sigma^2 = \sigma^2_0$ is true, then the test statistic $\chi_0^2$ follows the chi-square distribution with $n-1$ degrees of freedom. This is the reference distribution for this test procedure.

As with our other tests, we have:
- two-tailed tests, such as $H_1: \sigma^2 \neq \sigma_0^2$
- right-tailed test, such as $H_1: \sigma^2 \gt \sigma_0^2$
- left-tailed test, such as $H_1: \sigma^2 \lt \sigma^2_0$

To start, we'll use the rejection region method, where we use critical methods to reject or fail to reject the null hypothesis.

The right-tailed test is called that because the "rejection region" lies to the right; likewise, the left-tailed test has its rejection region to the left.

So, for each of our alternative hypotheses:
- $H_1: \sigma^2 \neq \sigma_0^2$ has a rejection criteria of $\chi^2_0 \gt \chi^2_{\alpha/2, n-1}$ or $\chi^2_0 \lt \chi^2_{1-\alpha/2, n-1}$
- $H_1: \sigma^2 \gt \sigma_0^2$ has a rejection criteria of $\chi^2_0 \gt \chi^2_{\alpha, n-1}$
- $H_1: \sigma^2 \lt \sigma^2_0$ has a rejection criteria of $\chi^2_0 \lt \chi^2_{1-\alpha, n-1}$

Of course, the main point here is to simply compare the test statistic (whose formula is given above) against the $\chi^2$ critical values, which are calculated in the same manner as when we were doing confidence intervals for variance. Select some $\alpha$, take a sample of size $n$, calculate the test statistic from the $S^2$ you get, and calculate the critical value. If your test statistic exceeds the critical value (that is, it lies in the rejection region), you have a strong result.,

> [!example]
>  Consider the test $H_0: \sigma^2 = 10$ against $H_1: \sigma^2 \neq 10$. What are the critical values for the test statistic $\chi_0^2$ with a significance level of $\alpha = 0.05$ and sample size $n = 18$?

This is a two-tailed test, so we need to develop two rejection regions - $\chi^2_0 \gt \chi^2_{\alpha/2, n-1}$ and $\chi^2_0 \lt \chi^2_{1-\alpha/2, n-1}$.

The first critical value, then, is $\chi^2_{0.025, 17}$, while the second critical value is $\chi^2_{0.975, 17}$.

> [!warning] On notation
> Again, remember that this represents the *percentage points* of $\chi^2$; if you want to use $\text{inv}\chi^2$, subtract from 1 so you get the region to the left instead of the region to the right.

We then find that the critical values are 2.56 and 30.19. Therefore, we reject the null hypothesis if the test statistic ends up being lower than 2.56 or greater than 30.19.

## Section 9.5
This addresses hypotehsis testing on proportions.

Many engineering problems tend to involve random variables that follow the binomial distribution, such as the proportion of defective products.

For example, consider testing
- $H_0: p = p_0$
- $H_1: p \neq p_0$

It is known that we can approximate the binomial distribution using the normal distribution. Thus, we can use rejection regions using critical values derived from the normal distribution.

The test statistic we use here is

$$Z_0 = \frac{\hat{p}-p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$$
where $\hat{p}$ is the sample proportion and $p_0$ is the prportion from the null hypothesis. As always, we can use either the p-value approach or the rejection region approach, where:
- under the p-value, we reject $H_0$ if the p-value $\leq \alpha$
- under the rejection region approach, we reject $H_0$ if the test statistic lies past the derived critical value(s) from $\alpha$ and $n$

> [!example]
> The proportion of defective products may not exceed 0.05, using $\alpha = 0.05$. If a manufacturer takes a random sample of 200 devices and finds that 4 of them are defective, what can we conclude?

Our claim is to test that $p \lt 0.05$. Then:
- $H_0: p = 0.05$
- $H_1: p \lt 0.05$

which amounts to a left-tailed test. Recall that $\alpha = 0.05$ and $n = 200$. $\hat{p} = 4/200 = 0.02$.

Applying our formula for $Z_0$ shows that our test statistic is equal to -1.95.

Using the p-value approach, we find that its corresponding area (to the left) is 0.026. And indeed, this is less than $\alpha$, so we reject $H_0$.

Alternatively, using the rejection region approach, we find the critical values in the same manner as the confidence interval; we find that our critical value is $-z_{\alpha}$ (for a left-tailed test), or $-z_{0.05} = -1.64$. Clearly, this falls in the rejection region, so we reject $H_0$. 

In turn, this means that we support $H_1: p \lt 0.05$.

> [!example]
> 545/1009 consumers said they were uncomfortable with drones delivering their purchases. Test the claim that most consumers are uncomfortable with drone deliveries with $\alpha = 0.05$.

Then, our hypotheses are:
- $H_0: p = 0.5$
- $H_1: p \gt 0.5$

which gives us a right-tailed test. Our test statistic is $Z_0 \approx 2.54$.

Again, using the p-value approach, we find that the p-value is 0.006, which is much less than $\alpha$, so we can reject $H_0$. Likewise, using the critical/rejection region approach, we find that $Z_{0.05} = 1.64$; again, the test statistic is more extreme.

So at the 5% significance level, we have strong evidence in favor of rejecting $H_0$, which is evidence in support of $H_1$ (note, however, that this is not equivalent to *accepting* $H_1$.)


