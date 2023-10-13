## Section 8.1
Recall that last time, we learned how to construct a confidence interval. 

In the previous example, we found that we were 95% confident that the mean impact energy was within a specific boundary, dictated by $\bar{x}$. We found this by applying

> [!tip] Two-sided confidence interval for $\mu$
> $$\bar{x} - z_{\alpha/2} *\frac{\sigma}{\sqrt{n}}\leq \mu \leq \bar{x} + z_{\alpha/2}*\frac{\sigma}{\sqrt{n}}$$

And it holds that as we increase the confidence level, the interval widens as well, since the critical value $z_{\alpha/2}$ widens. Of course, this can be less helpful if we're trying to look for $\mu$ in a wider range under the same confidence level and $\sigma$.

So in general, it is desirable to obtain a confidence interval that is short enough for decision-making purposes while also having adequate confidence. One way to achieve this is by choosing a larger sample size for $n$, which will yield better precision. 

Now, if it holds that the length of the confidence interval is

$$2*z_{\alpha/2}*\frac{\sigma}{\sqrt{n}}$$

then, of course, it holds that we should be able to find some $n$ for a desired confidence interval length.

The margin of error, $E$, can be expressed as $z_{\alpha/2}*\frac{\sigma}{\sqrt{n}}$, such that we can say that the length of the confidence interval is simply $2E$.

> [!tip] Desired sample size with specified error bounds
> In turn, if $\bar{x}$ is used to estimate $\mu$, we can be $100(1-\alpha)$% confident sure that the error $(\bar{x} - \mu)$ will not exceed a specified amount $E$ when the sample size is
> $$n = \left(\frac{z_{\alpha/2} * \sigma}{E}\right)^2$$

So supposing that we want an interval of length 1 (so $E$ is no more than 0.5), and we know that $\sigma = 1$ and our confidence level is 95% (and therefore $z_{\alpha/2} = 1.96$), plugging values in yields $n = 15.37$. Of course, round up to the next whole integer so that you get a 95% confidence level with an interval length less than 1.

### One-sided confidence bounds
The confidence interval we learned gives us bouth an upper and a lower confidence bound, giving us a two-sided confidence interval.

But we can also obtain one-sided confidence bounds by setting either bound to be $\pm \infty$, and then replacing $z_{\alpha/2}$ with $z_{\alpha}$. Why do we do this? It allows us to let the finite bound to be at some specific value, which can be more valuable in certain circumstances.

> [!tip] One-sided confidence bounds
> A $100(1-\alpha)$% upper-confidence bound for $\mu$ is 
> $$\mu \leq \bar{x} + z_{\alpha}*\frac{\sigma}{\sqrt{n}}$$
> and a lower-confidence bound of the same is
> $$\bar{x} - z_{\alpha}*\frac{\sigma}{\sqrt{n}} \leq \mu$$

You can compare this with two-sided confidence intervals. One gives you a better specific upper/lower bound, but the other actually gives you both an upper and lower bound.

To find $z_{\alpha}$, it is sufficient to just take the inverse normal for 0.9, 0.95, and 0.99; these describe $z$ from the infinite (left) bound rather than the mean, which is what we need.

![[Pasted image 20221102193034.png]]

## Section 8.3
We now move to the chi-square distribution. 

> [!tip] $\chi^2$ distribution
> Let $X_1, X_2, \ldots, X_n$ be a random sample from a normal distribution with $\mu$ and variance $\sigma^2$. Then the random variable
> $$X^2 = \frac{(n-1)S^2}{\sigma^2}$$
> has a chi-square ($\chi^2$) distribution with $n-1$ degrees of freedom.

>[!note] Degrees of freedom
>The degrees of freedom are the number of values in the statistic that are free to vary without influencing the result of the statistic.

Then define $\chi_{\alpha, k}^2$ as the percentage point or value of the chi-square random variable with $k$ degrees of freedom, such that the probability that $X^2$ exceeds this value is $\alpha$.

![[Pasted image 20221102193255.png]]

For example, if we wanted to find $P(\chi^2 \geq \chi^2_{0.05, 10})$, we can use a table to find that $\chi^2_{0.05, 10} = 18.31$.

> [!tip] Confidence interval for $\sigma^2$
> Then we may write 
> $$P(\chi^2_{1-\alpha/2, n-1} \leq X^2 \leq \chi^2_{\alpha/2, n-1}) = 1 - \alpha$$
> which amounts to constructing a confidence interval for the variance.
> 
> If $s^2$ is the sample variance from a random sample of $n$ observations from a normal distribution with unknown variance $\sigma^2$, then a $100(1-\alpha)$% confidence interval on $\sigma^2$ is
> $$\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}} \leq \sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}$$


> [!example]
> An automatic filling machine is used to fill bottles with liquid detergent. A random sample of 20 bottles results in a sample varaince of fill volume of $s^2 = 0.0153^2$. If the variance of fill volume is too large, and unacceptable proportion will be under or overfilled. We will assume that the fill volume is approximately normally distributed. Find a 95% upper confidence interval (two-sided and one-sided) for the variance of fill volume.

For the two-sided confidence interval, we will use
$$\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}} \leq \sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}$$
and we need $\chi^2_{0.025, 19}$ and $\chi^2_{0.975, 19}$. We will use a table to find these values. We end up with 8.91 and 32.85 (in that order). At this point, we only need to substitute the necessary values. This gives us

$$\frac{19*0.0153^2}{32.85}\leq \sigma^2 \leq \frac{19*0.0153^2}{8.91}$$

and taking square roots yields
$$0.0118 \leq \sigma \leq 0.0224 $$

> [!note] Finding the percentage points for (two-sided) $\chi^2_{\alpha, n-1}$
> Use the inverse $\chi^2$ function. In this case, you would plug in 0.025 and 0.975 (which are $\alpha/2$ and $1-\alpha/2$ respectively), with 19 degrees of freedom.
> 
> **WARNING** - It is important to note that the notation for $\chi^2$ uses the *percentage points* - the area to the **right** of the critical values, **not the area to the left** (which is what the inverse $\chi^2$ function on TI-nspires do). So to find $\chi^2_{0.025, 19}$, you would actually use $\text{inv}\chi^2(0.975, 19)$. 

> [!tip] One-sided confidence bound for variance
> It also holds there are one-sided confidence intervals for variance:
> $$\frac{(n-1)s^2}{\chi^2_{\alpha, n-1}} \leq \sigma^2$$
> $$\sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{1-\alpha, n-1}}$$

> [!note] Finding the percentage points for (one-sided) $\chi^2_{\alpha, n-1}$
> Use the inverse $\chi^2$ function. In this case, you would plug in 0.05 and 0.95 (which are $\alpha$ and $(1-\alpha)$ respectively), with 19 degrees of freedom.

