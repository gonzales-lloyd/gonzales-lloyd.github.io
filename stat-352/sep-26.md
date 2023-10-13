## Section 2.8
This section addresses Bayes' Theorem. 

Remember that conditional probabilities commonly provide the probability of an event, like failure, given a condition. But after a random experiment generates an outcome, we might be interested in the probability that a condition was present (like high contamination) given an outcome, like a semiconductor failure.

This question was resolved in the 1700s by Thomas Bayes. Let's take a spam email filter, for example.

Let's say that 20% of all emails are spam. The word "free" occurs in 60% of the spam messages, and 13% of the overall messages contain the word "free".

So if you receive an email containing the word "free", what is the probability that it's spam? In math notation, we have:
- P(spam) = 0.2
- P("free" | spam) = 0.6
- P("free") = 0.13

Recall the multiplication rule:
$$P(A \cap B) = P(B|A) * P(A)$$
from which Bayes' theorem follows:
$$P(A|B) = \frac{P(B|A)*P(A)}{P(B)}$$

so applying Bayes' theorem, we have
$$P(\text{spam | "free"}) = \frac{0.6*0.2}{0.13} = 0.923$$
So the likelihood that an email containing "free" is spam is pretty high, and should probably be thrown into the spam folder. Of course, this is not the only such condition.

Again, consider that we have a set in which:
- the probability of failure given high contamination is 0.1, $P(F|H)$
- the probability of high contamination is 0.2, $P(H)$
- the probability of failure given low contamination is 0.005,  $P(F|H')$
- the probability of low contamination is 0.8, $P(H')$

and suppose that we want to find the probability that if a failure occurred, it was the result of (or more accurately, associated with) high contamination. We can again apply Bayes' theorem:
$$P(H|F) = \frac{P(F|H)*P(H)}{P(F)}=$$

Assume that 1% of a population has cancer. We know from test results that if you take a test for cancer, the likelihood of:
- a true positive is 0.7
- a false positive is 0.2
- a negative test is 0.1

What is the probability that if you are given a positive test result, you actually have cancer?

We have:
- $P(C) = 0.01$
- $P(T|C) = 0.7$
- $P(T|C') = 0.2$

You can use Bayes' theorem here. But we can also use a different solution here.

Let's pretend we have 1,000 people in this population. We can actually develop a table for this:
|           | positive test | negative test | total |
| --------- | ------------- | ------------- | ----- |
| cancer    | 7             | 3             | 10    |
| no cancer | 990x0.02 = 198   | 792           | 990   |
| total     | 205           | 795              | 1000  |

So using this intuitive approach, we're looking atht the probability of cancer when the test result is positive. We end up with $P(C|T) = 7/205 \approx 0.034$.

This may seem low, particularly because $P(T|C) = 0.7$. But remember that we're considering this against the entire population - if, despite only 1% of the population having cancer, 20% of all test takers get a false positive, you can see that this may not be the most reliable test.

Remember that we previously talked about random experiments. A **random variable** is a **function** that assigns a real number to each outcoome in the sample space of a random experiement. Generally, a random variable is denoted by an uppercase letter such as $X$. After an experiment is conducted, we denote the measured value of the variable by a lowercase letter like $x = 70\,\mathrm{mA}$.

A **discrete** random variable is a random variable with a finite, countable range. Examples could be:
 - the number of scratches on a surface
 - the number of students at UNR

Pretend we toss a coin three times, with the random variable $X$ being the number of heads.

We have eight possible outcomes from tossing a coin three times. $X$ can be 0, 1, 2, or 3. Observe that $X$ takes on a value for each of the possible outcomes. But notice that the probability of each outcome is not equal. 
- 1 out 8 outcomes contain 0 heads.
- 3 out of 8 contain 1 head.
- 3 out of 8 contain 2 heads.
- 1 out of 8 contain 3 heads.

A **continuous** random variable is a random variable with an interval of real numbers for its range, like length, pressure, termpature, time, voltage, or weight. These can only be attained through measurement, not by counting. (At a physical level, sure, there may be a "smallest unit", but this is out of scope.)

Random variables help us model real events.

## Section 3.1
When we analyze random variables, we sometimes ignore the original sample space and focus on the probability distrubtion of the random variable. For example, pretend that $X$ were still the number of heads, but we instead threw the coin 1,000 times. Then, there are $2^{1000}$ outcomes in the sample space, at which point enumerating the sample space becomes unreasonable.

Instead, we will just focus on the probabilities. Suppose (in the original 3-coin example) that we develop a table with the probability distribution of $X$:

| $X$ | $P(X)$ |
| --- | ------ |
| 0   | 1/8    |
| 1   | 3/8    |
| 2   | 3/8    |
| 3   | 1/8    |

For discrete random variables, the distribution is often specified by such tables/lists. For continuous random variables and some other cases, it may be expressed as a formula.

> [!example]
> The time to recharge the flash on a camera is tested in three cellphones. The probability that a camera meets the recharge specification is 0.8; the cameras perform independently.
>
> What is the probability that the first and second cameras pass the test and the third one fails?

We simply calculate $0.8*0.8*0.2=0.128$, since these events are independent.

Consider $X$, which is equal to the number of cellphones meeting the recharge specification out of 3 cameras.

We can actually write out the probability of each outcome in the same space occurring, then adding up $X$ for each relevant event:
| Camera 1 | Camera 2 | Camera 3 | Probability | X   |
| -------- | -------- | -------- | ----------- | --- |
| P        | P        | P        | 0.512       | 3   |
| F        | P        | P        | 0.128       | 2   |
| ...         |          |          |             |     |

and after doing this and adding all the $X$s up, we find that our distrubtion is
| X   | P(X)  |
| --- | ----- |
| 0   | 0.008 |
| 1   | 0.096 |
| 2   | 0.384 |
| 3   | 0.512 |

We can also express probability distributions using graphs. For discrete random variables, this would essentially amount to a bar graph.

How do we formulate the distributions? We can do this using **probability mass functions**. For a discrete random variable $X$ with possible values $x_1, x_2, \ldots, x_n$, a probability mass function is a function such that
- $f(x_i) \geq 0$
- $\sum_{i=1}^{n}f(x_i) = 1$
- $f(x_i) = P(X=x_i)$

For example, pretend we have $f(x) = \frac{8}{7}*\left(\frac{1}{2}\right)^X$ for $X = 1, 2, 3$.

- By inspection, we can see that the first condition clearly holds.
- Adding up each number gives us $4/7$, $2/7$, and $1/7$, which gives us 1, so the second condition holds.
- The third condition is not possible to check with our given information, but we can intuitively determine that it is reasonably true.

Recall our probability distribution for the number of heads from tossing a coin three times:
| $X$ | $P(X)$ |
| --- | ------ |
| 0   | 1/8    |
| 1   | 3/8    |
| 2   | 3/8    |
| 3   | 1/8    |

You can see that the conditions hold for a probability mass function here. We will define $f(x)$ later.

An alternative way to describe a random variable's probability distribution is using cumulative probabilities, such as $P(X \leq x)$. For example, using the table above, if we were to evaluate $P(X \leq 2)$, we would get 0.875.

The cumulative distribution function fo a discrete random function $X$, denoted $F(x)$, is
$$F(x) = P(X \leq x) = \sum_{x_i \leq x} f(x_i)$$
You can see that this amounts to summing the probability mass function values for each outcome up to $x$, as desired. For example, you might want to find $P(X \leq 3)$. However, you could also find $1 - P(X \geq 4)$, assuming that $x$ is over integers, which is the probability for complimentary events. This holds because one of the conditions for the probability mass function is that its outputs add to 1.

So, some properties for the cumulative distribution function:
- $F(x) = P(X \leq x) = \sum_{x_i \leq x} f(x_i)$
- $0 \leq F(x) \leq 1$
- If $x \leq y$, then $F(x) \leq F(y)$.

Additionally, even if the random variable $X$ can only assume integer values, the cumulative distribution function is defined for noninteger values. For example, $P(X \leq 1.5) = P(X=0) + P(X=1)$. Actually, $P(X\leq 1.5) = P(X \leq x)$ for all $1 \leq x \lt 2$, given our assumption of $X$ above.


