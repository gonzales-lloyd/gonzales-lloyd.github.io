Remember that we have our cumulative distribution function, which describes the probability of getting a given value and any possible values less than that.
$$F(x) = \begin{cases}
0 & x \leq 0 \\
0.6561 & 0 \leq x \lt 1 \\
0.9447 & 1 \leq x \lt 2 \\
\ldots \\
1 & 4 \leq x
\end{cases}$$

## Section 3.3
After defining a discrete random variable, we will want the mean and variance to help us describe it.

The mean or expected value of the discrete random variable $X$ denoted $\mu$ or $E(x)$.
$$\mu = E(x) = \sum_x x*f(x)$$

Recall that $f(x)$ is the probability mass function, describing $P(X=x)$ for each possible $x$ that $X$ can take on.

Then, remember our example that if $X$ is the number of heads over three coin flips, then $X$ takes on a value in $\{0, 1, 2, 3\}$ with probabilities 1/8, 3/8, 3/8, and 1/8 respectively. Then, we can take the sum of multiplying those together and find we get 1.5, which is also what we intuitively expect.

Another interesting way of thinking about it is thinking of $f(x)$ as the distribution of loads on a really long stick, then $E(x)$ is the point at which the stick balances.

The variance of $X$ denoted $\sigma^2$ or $V(x)$, is

$$\sigma^2 = V(x) = \sum_x (x-\mu)^2*f(x)$$
or how the square of how much each (weighted) value deviates from the mean. The standard deviation is just $\sigma = \sqrt{\sigma^2}$. Most of the time, your data will fall within 1 standard deviation of the mean (see the 68-95-99.7 rule).

Things to note:
- You may have different variances for data with the same mean.
- You may have the same variances for data with the same mean, but the data is distributed differently.

Note that the units of any calculated variance is the original unit *squared*. 

There are a few things that we'll need to consider when evaluating random variables:
- Variability. If something is more variable, that tends to have more risk associated with it.
- The value of the mean. This means we expect higher values from higher values of $\mu$.

Whether we care more about variability or the mean varies from situtation to situation.

## Section 3.5
This section talks about **binomial distributions**.

A Bernoulli trial is a random experiment with exactly two possible outcomes. We assume that: 

- the trials that constitute the random experiment are independent; for example, flipping a coin once does not affect the second outcome.
- there are exactly two outcomes, "success" and "failure" - labels used to denote that something either did or did not happen
- the probability of success in each trial is constant

