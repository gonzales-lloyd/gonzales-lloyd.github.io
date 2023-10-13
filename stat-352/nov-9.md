## Section 9.1
Hypothesis testing is useful because many decisions in the real world can be expressed in terms of hypothesis testing problems.   In hypothesis testing, we discuss cooperative experiments involving a population, with our focus on testing hypotheses about the population parameters.  

For example, suppose your friend claims that their average drive of a golf ball is over 275 yards.  So you ask for substantiation – suppose they hit 25 drives.  Then what should be the mean of the 25 drives so that you're convinced?  What if it's 276 yards - then because it's barely over 275 yards, is that enough? Did they get lucky? What about 300 yards - maybe that's enough to convince us? What about 280?  

A statistical hypothesis is a statement about the parameters of one or more populations.  In this class, we'll address the parameters of the mean, variance, and proportion.  

Suppose that we need a rocket with a mean propellant burning rate of 50 centimeters per second.  The burning rate is a random variable that has a probability distribution; suppose we want to focus on the mean burning rate, a parameter of this distribution.  Formally:
- $H_0: \mu = 50$ cm per second 
- $H_1: \mu \neq 50$ cm per second 

$H_0$ is the null hypothesis.  This is the claim we initially assume to be true, and we always state it as an equality claim.  

$H_1$ is the alternative hypothesis, and is a statement that contradicts the null hypothesis.  It contains some inequality – $>$, $<$, or $\neq$ - where $\neq$ is a two-sided alternative claim.  We can also have one-sided right-tailed hypotheses, or $\mu > x$, and left-tailed hypotheses, or $\mu \lt x$. 

In general, the process is simple – assume the null hypothesis is true, do some calculations, and then decide whether to reject the null hypothesis.  (It's worth noting that the focus of hypothesis testing tends to be rejection or failing to reject the null hypothesis, not accepting the null hypothesis.)

A value of the sample mean $\bar{x}$ that falls close to the hypothesized value of $\mu = 50$ cm/s per second does not conflict with our null hypothesis.  A sample mean that is considerably different would instead support the alternative hypothesis.  In turn, the sample mean is the test statistic here.  

We now to define our decisions criteria – that is, under what cases do we reject the null hypothesis?  We might say that if our sample mean ends up being between 48.5 and 51.5, we fail to reject the null hypothesis; else, we reject it.  We'll describe how to pick the bounds later.  

Of course, it's possible to make errors, of which there are two types:
- A type I error is where we reject the null hypothesis when it is actually true.  
- A type II error is where we fail to reject the null hypothesis when it is actually false.  

The significance level $\alpha$ is equal to the probability of a type I error - that is, the probability of rejecting the null hypothesis when $H_0$ is actually true. Since the sampling distribution of the sample mean is normal under the central limit theorem, this amounts to having $\alpha/2$ on both sides of the normal distribution, at the tails.  

![[Pasted image 20221109133935.png]]

Now, suppose that the standard division of the burning rate is $\sigma = 2.5 \text{ cm/s}$ and that the burning rate has a distribution for which the conditions of the central limit theorem apply.  Then, the distribution of the sample mean is approximately normal with $\mu = 50$ and a standard deviation of $\frac{\sigma}{\sqrt{n}} \approx 0.79$. 

And if $\alpha$ represents the probability of rejecting when $H_0$ is actually true, this amounts to the probability of $\bar{X} \leq 48.5$ or $\bar{X} \geq 51.5$. In turn, we can simply normalize this and use the CDF of the normal distribution to find the area of $\alpha$. In this case, $\alpha \approx 0.0574$. 

It's worth noting that type I and type II errors are related; a decrease in the probability of one error increases the probability of the other error.  Generally, we're able to control $\alpha$, which is the probability of wrongly rejecting $H_0$; in turn, rejection of the null hypothesis is often considered a *strong conclusion.*

We choose to keep type I error low and type II error high because it's generally better to have type I error (in a practical sense). Suppose that a bank is deciding whether to lend money to somebody, and the null hypothesis is that the person defaults. Then, it's better to assume that somebody will default even if they won't (type II error), so that you don't just give out money. Assuming that somebody will not default and giving them money (type I error) is much riskier.

Of course, you can see how framing the question differently changes what type I error and type II error mean.  

Broadly speaking, the type I error is a measure of risk.  A widely used procedure in hypothesis testing is to pick a significance level of $\alpha = 0.05$, which has evolved through experience and may not be appropriate everywhere.  

We also have one-sided hypotheses, where if the objective is to make a claim involved statements such as "greater than", "exceeds", and so on, a entire-sided alternative hypothesis is more appropriate.  

If our claim in the burning rate problem was that the burning rate was "less than 50 cm/s" rather than "is 50 cm/s", we would have the following:
- $H_0 : \mu = 50$
- $H_1 : \mu \lt 50$ 

Notice how $H_0$ is still an equality statement.  In this case, perhaps we reject the null hypothesis if $\bar{X} \gt 51$, and fail to reject it otherwise (so if $\bar{X} \lt 51$.)

If we reject $H_0$, we have strong evidence in support of $H_1$. But if we fail to reject $H_0$, this is a *weak conclusion* - it's not the case that $H_0$ is true, but rather that we do not have strong evidence in support of $H_1$. 

So how do we find the rejection region, or the critical region, given $\alpha$?  In a two-sided test, this amounts to finding $z_{\alpha/2}$, which we have already found in two-sided confidence intervals, and applying it to the sampling distribution's standard deviation (which, for the sample mean, is found using the central limit theorem).

We also have something called the P-value, which is the smallest level of significance that would lead to rejection of the null hypothesis with the given data.  

**RESOLVE: last slides of 9.1**