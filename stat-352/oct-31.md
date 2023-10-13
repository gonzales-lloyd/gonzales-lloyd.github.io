> [!example]
> An electronics company manufactures resistors that have a mean resistance of 100 ohms and a standard devotion of 10 ohms.  The distribution of resistance is normal.  Find the probability that a random sample of $n = 25$ resistors will have an average resistance of fewer than 95 ohms.  

You might be inclined to jump straight to the normal distribution, applying something like a z-score and then calculating the CDF.  

But the problem is that we're taking a random sample of many resistors, not just one resistor.  So instead, we need to apply the central limit theorem, which appeals here since the population for the resistances exhibits a normal distribution.  

Note that *for each resistor*, $\mu = 100$ and $\sigma = 10$. But we want the average resistance over 25 resistors, the random variable $\bar{X}$. It's important to note that $\mu_x = 100$; the mean of the sampling distribution remains the same.

But the standard distribution is equal to $\sigma_x = \frac{10}{\sqrt{25}} = 2$. So instead, we want to find the area less than 95 for $N(100, 2)$ - not $N(100, 10)$.

> [!info]
> Note: the expression for the standard deviation comes from the bottom part of the central limit theorem. It's also an innate formula on its own:
> $$\sigma_x = \frac{\sigma}{\sqrt{n}}$$
> for $n$ samples over a population with a standard deviation of $\sigma$.
> And here's the central limit theorem:
> $$Z = \frac{\bar{X}-\mu}{\sigma/\sqrt{n}}$$

And after normalizing for the z-score, we find that the probability that the average resistance of 25 resistors is less than 95 ohms is 0.0062, with a z-score of -2.5.

> [!example]
> The probability density function of a random variable $X$ is given below. Find the distribution of the sample mean of a random sample of size $n = 40$.
> $$f(x) = \begin{cases}1/2, &4 \leq x \leq 6 \\ 0, &\text{otherwise}\end{cases}$$

Obviously, this is not normally distributed. But since $n = 40 \gt 30$, we can apply the central limit theorem.

First, we'll need to find the mean of the distribution as a whole, which will also be the mean in our CLT approximation.

$$\mu = \int_4^6 \frac{1}{2} \, \mathrm{d}x = 5$$

$$\sigma^2 = \int_4^6 \frac{1}{2} \, \mathrm{d}x - 5^2 = \frac{1}{3}$$

and by the central limit theorem, we get a probability distribution for $\bar{X}$ with $n = 40$ where $\mu_x = \mu = 5$ and $\sigma_x = \frac{\sigma}{\sqrt{n}}=\frac{1/{\sqrt{3}}}{\sqrt{40}}$.

## Section 8.1
This addresses the confidence interval on the mean of a normal distribution. The idea is that we don't know the population mean $\mu$, but we do have a sample mean $\bar{x}$ - how do we estimate an interval $\mu$, and how do we express how confident we are that $\mu$ is within that interval?

You can estimate a variety of population parameters, but we'll estimate $\mu$ here. But a single value of $\bar{x}$ doesn't tell us much about how close it is to the true value of the population mean $\mu$.

A confidence interval always specifies a confidence level, usually 90%, 95%, or 99%, which is a measure of the reliability of the procedure.  By reliability, we mean that if we repeated this experiment over and over again, 95% of all samples would produce a confidence interval containing the true population mean.  

Suppose that we found out that $\bar{x} = 1000$. But is $\mu$ more likely to be between 900 and 1100, or between 990 and 1010?

An interval estimate for a population parameter is called a confidence interval.  Information about the precision of estimation is conveyed by the length of the interval.  A short interval implies precise estimation.  

The confidence interval is constructed so that we have high confidence that is contains the unknown population parameter.  So why don't we just make a high confidence interval?  It gives us less precision; we're 100% certain that the population mean is somewhere between $-\infty$ and $\infty$, but that's not very helpful.  A similar tradeoff exists if we reduce the confidence interval to get better precisions.

Now, given that the central limit theorem gives us normal probability distributions, it holds we can express 95% confidence in terms of an area of 0.95 over the corresponding normal distribution. 

> [!warning]
> $\alpha$ is equal to 1 minus the confidence level! So a confidence level of 95% yields $\alpha = 0.05$. This needs to be fixed everywhere applicable.
> 
> (This is because $\alpha$ corresponds to the probability of *exceeding* the critical values.)
> ![[Pasted image 20221107132016.png]]

In verbose terms, we may write
![[Pasted image 20221031140456.png]]

That is - given some confidence level $\alpha$, the value of $\bar{X}$ (which we believe to be an estimate of $\mu$) will generate a probability distribution under the central limit theorem $N(\bar{X}, \frac{\sigma}{\sqrt{n}})$, such that $\mu$ is in between the corresponding $z$ values for $\alpha$ some percentage of the time (falling outside of it $100*\alpha$ percent of the time). 

More generally, this describes the probability with which a $\bar{X}$ generates an  interval for which $\mu$ is within, supposing this were repeated many times under the same $\sigma$ and $n$.

It's worth noting that $-z_{\alpha/2}$ and $z_{\alpha/2}$ are what we call critical numbers, $-z_{0.025}$ and $z_{0.025}$ for a 95% confidence interval.

Generally speaking, we use a table for finding the critical numbers:

![[Pasted image 20221102191852.png]]

though these critical values can be found "manually", in that these are equivalent to the z-scores for the areas of 0.9, 0.95, and 0.99 centered about the mean of the normal distribution. If tables aren't available, simply do the inverse normal of $(1-\alpha)+\frac{\alpha}{2}$ to find these critical values. For example, finding the critical value for a two-sided 90% confidence interval amounts to finding the z-score corresponding to an area of 0.95, since this is where the *right* edge of the two-sided interval is.