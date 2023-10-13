Recall the binomial distribution. a random experiment consists of $n$ Bernoulli trials such that:
- The trials are independent.
- Each trial results in only two possible outcomes, either "success" or "failure".
- The probability of a success in each trial, denoted $p$, is constant.  

The random variable $X$ that equals the number of trials that result in a success is a binomial random variable with parameters $0 \lt p \lt 1$ and $n = 1, 2, \ldots$ . The probability mass function of $X$ is 

$$f(x) = {n \choose x} p^x (1-p)^{n-x}$$

for $x = 0, 1, \ldots, n$. This is where $p$ is the probability of success, and $1 - p$ is the probability of failure.  

${n \choose x}$ refers to the number of outcomes with exactly $x$ successes among $n$ trials. The remaining terms, $p^x (1-p)^{n-x}$, refers to the probability of $x$ successes among $n$ trials in a row in any one particular order.

> [!example]
> Each sample of water has a 10% chance of containing a particular organic pollutant.  Assume that the samples are independent with regard to the presence of the pollutant.  Find the probability that in the next 18 samples, exactly 2 contain the pollutant.  

Here, we define a "success" as a sample containing the pollutant.

$X$ is the number of samples that contain the pollutant in the 18 samples analyzed. $p = 0.1$, and $n=18$. We want two successes, so $x = 2$>

Then, we have 
$$P(X=2) = f(2) = {18 \choose 2}*0.1^2*(1-0.1)^{18-2} = 0.284$$

> [!example]
> Under the same conditions above, find the probability that in 18 samples, at least two contain the pollutant.  

If we want to compute this, we want to find $P(X \geq 2)$, which we happen to know that $X$ takes on integer values between 0 and 18. This is important because by definition of the binomial distribution, we must have integer values.  

So this is equivalent to just finding $P(X=2) + P(X=3) + \cdots + P(X=18)$. But we can simply take the complement and note this is equal to finding $1 - P(X \lt 2)$.  Then we have $1 - P(X=1) - P(X=0)$, so we only have to compute two probabilities using the binomial distribution formula.

> [!example]
> Under the same conditions above, find the probability that $3 \leq X \lt 7$.

The process is to simply find $P(X=3) + \cdots + P(X=6)$. The calculations are the same as above.

---
It turns out we can calculate mean and variance using $p$ and $n$ directly for a **binomial random variable** (not any old random variable!):

$$\mu = E(x) = np$$
$$\sigma^2 = V(x) = np(1-p)$$

so the mean and variance in the conditions above are $\mu = 1.8$ and $\sigma^2 = 1.62$ respectively.

## Section 3.8
The Poisson distribution is one other spatial distribution in chapter 3, like the binomial distribution.

A widely used distribution emerges from the concept that events occur randomly in an interval, or more generally, in a region.  The random variable of interest is the count of events that occur within the interval.  

A Poisson distribution does not have a given number of trials (or $n$) like the binomial distribution does.  For example, where a binomial experiment might be used to determine how many red cars are in a random sample of 50 cars, a Poisson experiment might focus on the number of cars arriving at a car wash in a 20-minute interval.  

The binomial distribution describes a distribution of two possible outcomes designated as successes and failures from a given number of trials.  

The Poisson distribution focuses only on the number of discrete occurrences over some interval, or more generally, in a region.  

A discrete random variable $X$ is said to have a Poisson distribution with parameter $\lambda \gt 0$ if the probability mass function of $X$ is given by
$$f(x) = \frac{\lambda ^x * e^{-\lambda}}{x!}$$
for $x = 0, 1, 2, \ldots$. 

$x$ is the number of occurences; $\lambda$ is the mean number of occurrences in the interval.  

The Poisson distribution has the following characteristics:
- It is a discrete probability distribution.  
- Each occurrence is independent of the other occurrences.  
- It describes discrete occurrences over an interval.  
- The mean number of occurrences must be constant throughout the experiment.  

> [!example]
> Births in a hospital occur randomly at an average rate of 1.8 births per hour.  Suppose that the number of births follows a Poisson distribution.  What is the probability of observing 4 births in a given hour at the hospital?  

Here, we have $\lambda = 1.8$ and $x=4$.  Using the formula gives us 0.072, or we can use an Nspire with `poissPdf(1.8, 4)`. 

> [!example]
> Suppose the number of flaws in a wire follows a Poisson distribution with a mean of 2.3 flaws per millimeter.  What is the probability of 10 flaws in 5 millimeters of wire?

Something to note is that we're given the average number of flaws per millimeter, but $X$ refers to the number of flaws in 5 millimeters of wire.  So to find $\lambda$ for $x$, we must multiply the mean by 5 to get a valid $\lambda$ for our random variable.

We find that the probability is 0.113.

> [!example]
> Under the same conditions above, determine the probability of at least one flaw in 2 millimeters of wire.  

Since $X$ considers itself to be over 2 millimeters, we multiply the average per millimeter by 2 so that we have $\lambda = 4.6$.

We need 
$$P(X \gt 1) = \sum_{X=1}^{\infty} \frac{e^{-\lambda} \lambda^x}{x!}$$
but clearly this is not very easy to calculate, so instead we can take the complement and instead take $1 - P(X \lt 1)$, which is equal to $1 - P(X=0)$ since Poisson distributions are lower-bounded by 0.

Then we find that we have a probability of 0.9899.

Worth noting is that if $X$ is a Poisson random variable with parameter $\lambda$, then 
$$\mu = E(x) = \lambda$$
and 
$$\sigma^2 = V(X) = \lambda$$
