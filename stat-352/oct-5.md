## Section 4.1
We now turn to continuous random variables.

For example, temperature, time, voltage, weight, and length are all continuous.

Consider a survey that finds the following distribution for the age of a rented car:
| Age (years) | Probability |
| ----------- | ----------- |
| 0-1         | 0.2         |
| 1-2         | 0.28        |
| 2-3         | 0.2         |
| 3-4         | 0.15        |
| 4-5         | 0.1         |
| 5-6         | 0.07            |

(Note that the upper bound is exclusive, e.g. "0-1 years" is $0 \leq x \lt 1$.)

You might commonly represent this as a histogram. These represent relative frequencies. But instead, we might connect the points using smooth curves, such that we have what is known as a *density curve*.

For a continuous random variable $X$, a probability density function is a function such that:
- $f(x) \geq 0$
- $\int_{-\infty}^{\infty} f(x) \mathrm{d}x = 1$
- $P(a \leq X \leq b) = \int_a^b f(x) \mathrm{d}x$, which is also equal to the area under $f(x)$ from $a$ to $b$ for any values $a$ and $b$.

Notice how the last condition is analogous to how we use summations in discrete random variables, which have probability mass functions.

So for the example above, if we want to find $P(1 \leq X \leq 3)$, we will get 0.28 + 0.2.

An important fact is that we can only evaluate the probability of a continuous random variable $X$ only for an interval of values; $P(X = x) = 0$ for any $x$. 

The reason of this is that the area under the curve of a specific value is 0; when evaluating $\frac{1}{x}$, taking the limit as $x \rightarrow \infty$ gives us 0.

Another thing worth noting is that whether considering strict or non-strict inequality, the probability is the same:
$$P(x_1 \leq X \leq x_2) = P(x_1 \lt X \lt x_2)$$
Note, though, that this only holds true for continuous random variables; not (necessarily) discrete random variables!


Suppose that $X$ is a continuous random variable whose probability density function is $3x^2$ for $0 \lt x \lt 1$.

We can show that $f(x)$ is a probability density function by applying each of the testable conditions:
- indeed, $3x^2 \geq 0$ for all values of $x

Testing that $\int_{-\infty}^{\infty} 3x^2 \mathrm{d}x =1$ requires that we split the integral into several separate bounds:

$$
\begin{align}
\int_{-\infty}^{\infty} 3x^2 \mathrm{d}x &= \int_{-\infty}^0 3x^2 \mathrm{d}x + \int_{0}^1 3x^2 \mathrm{d}x + \int_{1}^\infty 3x^2 \mathrm{d}x\\
&= 0 + \left.\frac{3x^3}{3}\right|_0^1 + 0\\
&= 1^3 -0^3 \\
&=1
\end{align}
$$
So we find that it is true. Note that because the probability density function is "not defined" beyond $0 \lt x \lt 1$, then we can replace $3x^2$ to be $0$ in the improper integrals, giving us 0s.

It's important to note that $f(x)$ is only define from 0 to 1. For example, if we're asked for $P(x \gt 0.6)$, our integral bounds are not from $0.6$ to $\infty$; they're from $0.6$ to $1$. 

> [!example]
> Let $X$ represent the current measured in a copper wire in milliamperes. Assume that the range of $X$ is $[4.9, 5.1]$, and that its PDF is $f(x) = 4.9 \leq x \leq 5.1.$. What is the probability that a current measurement is less than 5 mA?

(Note that we can confirm this is a PDF by taking $\int_{4.9}^{5.1} 5 \mathrm{d}x$, noting that the value of the function is implied to be 0 everywhere else.)

To find $P(X \lt 5)$, we simply evaluate $\int_{4.9}^{5} 5 \mathrm{d}x =0.5$.

---

It also holds that cumulative distribution functions, or CDFs, for continuous random variables exist as well:

$$F(x) = P(X \leq x) = \int_{-\infty}^{x} f(u) du$$

Suppose we want to create a CDF for the previous question. Then we would find that for $x \lt 4.9$, it would yield 0, and for $x \gt 5.1$, it would yield 1.

Then, we would need to find 
$$
\begin{align}
\int_{-\infty}^x f(u)\mathrm{d}u &= \int_{4.9}^x5\mathrm{d}u\\
&= \left.5u\right|_{4.9}^x\\
&= 5x-24.5
\end{align}
$$

So our CDF is 
$$F(x) = \begin{cases}
0 & x\lt 4.9\\
5x-24.5 & 4.9 \leq x \lt 5.1 \\
1 & x \gt 5.1
\end{cases}$$


Given a cumulative distribution function $F(x)$, then
$$f(x) = \frac{\mathrm{d}F(x)}{\mathrm{d}x}$$
as long as the derivative exists. This follows from the fundamental theoerem of calculus; to obtain the PDF, we simply take the derivative of the CDF.

> [!example]
> We have a CDF expressed by $1-e^{-0.01x}$ for $0 \geq x$ (and 0 everywhere else). What is the PDF of $X$?

We simply take the derivative. For $x \lt 0$, its derivative is simply 0. Elsewhere, we have $0.01e^{-0.01x}$.

If we need to find intervals, we may use the PDF or use the CDF (possibly by subtracting from 1 or from other CDF evaluations).

Suppose that $X$ is a continuous random variable with PDF $f(x)$. Then its mean (or expected value), denoted $\mu$ or $E(x)$, is

$$\mu = E(x) = \int_{-\infty}^{\infty} x*f(x) \mathrm{d}x$$
Applying $f(x)=5$ for $[4.9, 5.1]$, for example, gives us

$$\int_{-\infty}^{\infty} x*f(x) \mathrm{d}x=\int_{4.9}^{5.1} x*5 \mathrm{d}x$$
and you will find this simply gives you 5.

The variance of a continuous random variable $X$ is given by
$$\sigma^2 = V(x) = \int_{-\infty}^{\infty}(x-\mu)^2 *f(x)\,\mathrm{d}x = \int_{-\infty}^{\infty}x^2 *f(x)\,\mathrm{d}x - \mu^2$$

and its standard deviation is simply $\sigma = \sqrt{\sigma^2}$. 