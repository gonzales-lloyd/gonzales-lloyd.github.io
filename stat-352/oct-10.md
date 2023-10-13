## Section 4.5
We now move to the normal distribution, a special form of continuous probability distribution.

It fits many natural phenomena, such as blood pressure, heights, IQ scores, and measurement error. It is also known as the Gaussian distribution.

The probability density function of the normal distribution is bell-shaped and symmetric. That is to say, things are more likely towards the mean $\mu$ which is also the highest value in the PDF.

As with other PDFs, we can take an integral between two values to find the percentage (more accurately, the proportion of entities) that fall within those two values.

The PDF of a normally distributed continuous random variable $X$ is 

$$f(x) = \frac{1}{\sqrt{2 \pi} * \sigma}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$$
for all real numbers. $\mu$ is the mean, and $\sigma \gt 0$ is the standard deviation. Then it holds that $E(X) = \mu$ and $V(X) = \sigma^2$.

Given that we have two paremeters, we may use the notation $N(\mu, \sigma^2)$ to denote the distribution. For example, $N(1, 4)$ denotes a mean of 1 and a variance of 4.

You can tell that there are infinitely many normal distributions, because there are infinitely many parameters. Changing $\mu$ changes the location of the curve; increasing $\sigma$ flattens the curve. 

Worth noting is that there is no closed-form expression for the integral of a normal PDF, so we usually find probabilities using the numerical method or from a table. (That is - we don't compute the integral of $f(x)$ to figure out $P(a \leq X \leq b)$.)

A special normal distribution is $N(0, 1)$ - that is, $\mu = 0$ and $\sigma^2 = 1$. This is called a standard normal random variable denoted $Z$. The cumulative distribution function of a standard normal random variable is denoted
$$\Phi(z) = P(Z \leq z)$$
Then, for example, $\Phi(1.5) = P( Z \leq 1.5)$. If we wanted to find $P(-0.5 \leq Z \leq 1.5)$, we would need to evaluate a rather difficult integral. Instead, we can use a table that gives us the cumulative probabilities for a *standard normal random variable*.

The table ranges from z-scores (standard deviations) of -3.99 to 3.99. Each row represents one specific z-score for a specific tenth; the columns represent a specific hundredths value. Again, remember that this gives us cumulative probabilities. This means we may have to subtract two values from the table or apply the complement rule to find specific probability intervals.

Suppose we want to find $P(Z \geq 1.26)$. Then, we find the value for a z-score of 1.26, and then subtract that from 1 - that is, $1 - \Phi(1.26) = 1 - P(Z \leq 1.26)$. Notice that the z-score is 1.26 because we are working with a standard normal random variable.

But because the standard normal distribution is symmetric about 0, notice that $P(Z \geq 1.26)  = P(Z \leq -1.26)$. This means we can avoid applying the complement if we want.

Similarly:
$$P(Z \gt -1.37) = 1- P(Z \leq -1.37) = P(Z \lt 1.37)$$

As with other CDFs, you can always subtract two CDF values from each other to find an interval.

Generally speaking, we only deal with the values between -3 and 3 (three standard deviations), because anything past that is an outlier with relatively small values.


For probabilities with z-scores less than -3.99, we can say that such probabilities are less than 0.000033. The same goes for extreme probabilities greater than 3.99.

Suppose that we want to find the value z such that $P(Z\geq z) = 0.05$. It is unlikely we will find a z-score that gives us the exact probability of 0.05, so we can instead find the closest listed z-score near 0.05.

What if we want to find the value $z$ such that $P(-z \lt Z \lt z) = 0.99$? Since we are looking for an identical $z$ and the normal distribution is symmetric, this is equivalent to finding $P(-z \lt 0) + P(0 \lt z) = 0.99$. Notice that this implies that the areas on both sides is 0.005; this means that such a z-score must begin at 0.005. 

For any normal random variable with mean $\mu$ and variance $\sigma^2$, we can find the z-score by simply applying $z = \frac{x-\mu}{\sigma}$, which is the z-score obtained by "standardizing" $x$.

> [!example]
> Suppose that the current measurements in a strip of wire are assumed to follow a normal distribution with a mean of 10 mA and a variance of 4 mA^2. What is the probability that a measurement exceeds 13 millamperes?

The first step is to figure out the z-score of a measurement of 13:

$$z = \frac{13-10}{2}=1.5$$

and since we want to find the probability a measurement exceeds 13 mA, we can find $1 - \Phi(1.5)$.
