We found that we could readily find the z-score of any arbitrary normal random variable by standardizing a known normal random variable $X$ into $Z$:

$$Z = \frac{X-\mu}{\sigma}$$
(which can be done using `invnorm()` on a calculator.)

> [!example]
> $\mu$ = 10 milliamperes and $\sigma$ = 2 milliamperes.  What is the probability that a current measurement is between 9 and 11 milliamperes?  

One way to do this is by calculating the z-scores for 9 and 11 milliamperes for this particular normal distribution.  That gives us z-scores of -0.5 and 0.5, respectively.  Using a table gives us 0.3830.

Of course, we could always take the integral and calculate the area under the curve directly by using `normCdf()`, which gives 0.3829 instead.  

> [!example]
> Using the same parameters above, what is the value for which the probability that a current measurement is less than this value is 0.98?

In a direct sense, you could use calculator functions.  

But by hand, we can do this by finding what z-score in the table corresponds to 0.98 (as a CDF, since we're looking for $X \lt 0.98$), then reverse the z-score formula to find what value of $X$ with our given $\mu$ and $\sigma$ gives us 0.98.

We find that the z-score is 2.05, and by applying the z-score formula:

$$2.05 = \frac{x-10}{2}$$

We find that $x = 14.1$, such that 98% of all current measurements will be less than 14.1 milliamperes.  

## Section 4.6
This section covers a normal approximation to the binomial distribution.  

For many physical systems, the binomial model is appropriate with a very large value of $n$.  But in such causes, it can be difficult to calculate probabilities by using the binomial distribution.  Fortunately, it is effective to use the normal distribution instead.  

Recall that the binomial distribution is discrete, but it is also (somewhat) accurately modeled by the normal distribution at specific values:
![[Pasted image 20221012184723.png]]

You can see that if we were to take the area under the curve of the normal distribution up to some specific discrete value, it would approximate the total probability represented by the (area of the) bars in the binomial distribution.  But we need some way to convert our discrete parameters $n$ and $p$ into our continuous parameters $\mu$ and $\sigma$. It turns out that we have formulas that will do this for us.

> [!tip] Formula
> To convert from $n$ and $p$ for a binomial random variable $X$ and approximate it using some normal random variable in terms of $\mu$ and $\sigma$:
> $$\mu = n * p$$
> $$\sigma^2 = n*p*(1-p)$$

Suppose that for the graph depicted, we wanted to find the probability that $P(3\leq X \leq 7)$. With the approach we know, we would have to take the sum of the areas of the bars from $x=3$ to $x=7$. But suppose that we have 1,000 trials.  Then, we would need to sum over many hundreds of elements, which is not practical without a calculator.  

Instead, we can use the normal distribution to make an approximation.  Now, you might notice something here - if we wanted to estimate $P(3\leq X \leq 7)$, then we could use the normal distribution from 3 to 7, or we could take it from 2.5 to 7.5. If we use 3 to 7, we will be underestimating; this is because we'll lose half of the last two bars that we would sum up if we were calculating this exactly.  So instead, we take the normal distribution from 2.5 to 7.5.

We use a modified interval to better compensate for the difference between the continuous normal distribution and the discrete binomial distribution.  We refer to this modification as a continuity correction.  

> [!example]
> Assume in a digital communication channel, the number of bits received in error can be modeled by a binomial random variable.  Assume that the probability that a bit is curved in error is $1 \times 10^{-5}$. If 16 million bits are transmitted, what is the probability that 150 or fewer errors occur?  

Applying the conventional formula for the CDF of a binomial variable:

$$P(X\leq n) = \sum_{x=0}^{n}{16,000,000 \choose x}*(10^{-5})^x*(1-10^{-5})^{16,000,000-x}$$

Obviously we can see that would be pretty hard to compute for a human, and fairly difficult using a calculator.  (An N-spire isn't able to calculate this using `binomCdf()`. You can also see that taking something to the 16 millionth power isn't a trivial task either, without making some assumptions.)

Instead, we have a new formula.

> [!tip] Formula
> If $X$ is a binomial random variable with parameters $n$ and $p$:
> $$Z = \frac{X-np}{\sqrt{np(1-p)}}$$
> then $Z$ approximately represents a standard normal random variable.  

Remember, this is an approximation: we are transforming from the discrete to the continuous, an imperfect process.  This gives us a curve that approximates the heights of the bars at nonzero integer values.  

Additionally, to approximate a binomial probability with a normal distribution, we must apply a continuity correction:

> [!tip] Continuity correction for normal approximation to binomial probabilities
> For $np \gt 5$ and $n(1-p) \gt 5$,
> $$P(X \leq x) = P(X \leq x + 0.5) \approx P\left(Z \leq \frac{x+0.5-np}{\sqrt{np(1-p)}}\right)$$
> $$P(X \geq x) = P(X \geq x - 0.5) \approx P\left(Z \geq \frac{x-0.5-np}{\sqrt{np(1-p)}}\right)$$
> **Note that non-strict inequality is required!**

Notice that the above implies that $P(X \leq 70) = P(X \leq 70.5)$. This is a true statement, because remember we're trying to approximate discretes; this is actually a true statement if $X$ is binomial. (Obviously it is not actually true if we think $X$ is normal - the areas will be different for continuous variables.)

Finding the probability on the right sides of the expressions is easy, because note that $Z$ is a *standard* normal random variable; therefore, evaluating the big scary fraction gives us a z-score that we can directly look up in the table (and apply additional subtractions/additions on.)

So going back to our question, we find that we want to find $P(X\leq 150)$. We can use a normal approximation after verifying that the conditions $np \gt 5$ and $n(1-p) \gt 5$ hold, which they do.

Then, note that 

$$P(X \leq x) = P(X \leq x + 0.5) \approx P\left(Z \leq \frac{150+0.5-(16,000,000)(1 \times 10^{-5})}{\sqrt{(16,000,000)(1 \times 10^{-5})(1-10^{-5})}}\right)$$
(if you want to simplify it by hand, note that $n*p = 160$ which can be substituted as needed)

We find that the z-score for this is -0.75, or $P(X \leq 150) \approx (Z \leq -0.75)$. For this z-score, the CDF is equal to 0.227. This is an approximation, of course.

---

Earlier, we mentioned that it was important to have non-strict inequality.  What if we have strict inequalities instead, like $P(X \lt 150)$? Remember that for discrete values, strictness matters; for continuous variables, strictness does not matter.  

Notice that as a discrete variable, $P(X \lt 150) = P(X \leq 149) = P(X \leq 149.5)$. Then, we can apply our formulas just like before.  

> [!example]
> Assume that in a digital communication channel, the number of bits received in error can be modeled by a binomial random variable, and assume that the probability that a bit is received in error is 0.1.  If 50 bits are transmitted, what is the probability that two or fewer errors occur?  

For the sake of demonstration, we can apply our normal approach to finding a binomial CDF by hand, but we can also make an approximation with the normal distribution.  

$$P(X \leq 2) = P(X=0) + P(X=1) + P(X=2)=0.112$$

Assuming that the conditions for a normal approximation of a binomial distribution hold, then:

$$P(X\leq 2) = P(X \leq 2.5) \approx P\left(Z\leq \frac{2.5-50*0.1}{\sqrt{50*0.1*0.9}} \right)$$
which gives us a z-score of -1.18, and using a table to find $P(Z \leq -1.18)$, we get 0.119.

> [!example]
> Using the same parameters above, what is the probability that exactly five errors occur?  

Notice that this is equivalent to finding $P(5 \leq X \leq 5) = P(4.5 \geq X \geq 5.5)$ using our approximation approach.  It turns out we'll get $P(-0.24 \leq X \leq 0.24)$ after applying the z-score calculations for approximation. This in turn is equal to $P(Z \leq 0.24) - P(Z \leq -0.24)$, and we find 0.19 as our approximated value from using a table.

Worth noting is that the exact value is equal to 0.1849 from the binomal distribution formula.





