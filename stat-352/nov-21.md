## Section 9.2
This section addresses tests on the mean of a normal distribution where the variance is known.

We consider hypothesis testing about the mean $\mu$ of a single normal population where the variance of the population $\sigma^2$ is known. We assume that a random sample $X_1 \ldots X_n$ is taken from the population. Based on our previous discussion, the sample mean $bar{X}$ is an unbaised point estimator of $\mu$. 

We know that the sampling distriubtion of $\bar{X}$ is normal with meanu $\mu_0$ and standard deviation $\sigma/\sqrt{n}$ if the null hypotehsis is true.

We can calculate a P-value or construct a critical region based on the computed value of the sample mean $\bar{X}$. 

It is necessary to standardize the test statistic. To standardize any variable, we subtract from the mean and divide by the standard variance (which we know, since the population variance is known.) So taking $\mu_0$ from the null hypothesis, we have
$$Z_0 = \frac{\bar{X} -\mu_0}{\sigma/\sqrt{n}}$$
$\bar{X}$ is the test statistic; then $Z_0$ is the standardized test statistic.

So to test our hypothesis on the man:
- Take a random sample of size $n$ and compute the value of the sample mean $\bar{X}$.
- Compute the standardized test statistic as described above.
- If taking the P-value approach, find the P-value.
- Using the fixed significance level approach, construct the rejection region.
- Conclude the test with either rejecting $H_0$ or failing to reject $H_0$ based on whether the P-value is sufficiently low or if the standardized test statistic lies within the rejection region.

> [!example]
> The mean burning rate of a propellant must be 50 cm/s. The standard deviation is known to be $\sigma = 2$ cm/s. The experimenter decides to specify a type 1 error probability (significance level) of $\alpha = 0.05$ and selects a random sample of $n=25$, finding an average burning rate of $\bar{x} = 51.3$.
>
> What conclusions should be drawn?

Then since our parameter of interest is $\mu$, our hypotheses are:
- $H_0: \mu = 50$
- $H_1: \mu \neq 50$

We normalize the test statistic:

$$Z_0 = \frac{51.5-50}{2/\sqrt{25}}=3.25$$

We now state that we reject $H_0$ if the P-value is less than 0.05. (If we use a fixed signifcance level test, the boundaries of the critical region would be $-z_{0.025} = -1.96$ and $z_{0.025} = 1.96$.)

We then discover that the P-value is equal to $2*z=2*0.00056 = 0.0012$ - that is, assuming $H_0$ is true, the probability that we observe a mean of $\mu = 51.5$ or more extreme is 0.0012.

Therefore, since the P value is less than or equal to $\alpha$, we reject $H_0$. 

If we instead take the rejection region approach, we find that (from table 3) the associated z-scores are -1.96 and 1.96. So the rejection regions are anything *outside* of those z-scores; our test statistic was, again $Z_0 = 3.25$. This is well within the rejection region, so we reject the null hypothesis. 

In other words, our conclusion is that we support $H_1: \mu \neq 50$. The interpretation of this is that there is strong evidence that the mean burning rate differs from 50 cm/s, based on a sample of 25 measurmeents.  