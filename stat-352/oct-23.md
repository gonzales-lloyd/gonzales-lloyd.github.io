## Section 6.1
This chapter addresses descriptive statistics, which addresses the structure of the data. We're not as concerned about the entire data, but rather certain descriptions of the data like summary statistics.

The **population** refers to the complete collection of all measurements or data that are being considered. A **sample** is a subcollection of members selected from a population.

In a practical example, it'd be pretty hard to get the salaries of every engineer in the US. But instead, you can randomly select a few so that you get a sample instead. Often, a sample of 1,000 is sufficient to estimate the qualities of a population of 20,000,000. It actually turns out that the size of the population doesn't matter; what matters is the size of your sample and whether you've actually managed to get a random sample.

If your sample isn't random and large, obviously it won't be very representative. If you take the salary of the top engineer at Google, or if you take the salaries of a bunch of Silicon Valley engineers, it's not going to represent the whole US.

If the $n$ observations in a sample are denoted by $x_1, \ldots, x_n$, the **sample mean** is

$$\bar{x} = \frac{x_1+\cdots+x_n}{n}=\frac{\sum_{i=1}^{n}x_i}{n}$$

Note that this is **NOT** the same as the **population mean**, $\mu$, which has an identical formula over the $N$ members of the population.

In general, our goal is to estimate $\mu$ using $\bar{x}$, since $\mu$ is typically not known for a population.

The sample variance is

$$s^2 = \frac{\sum_{i=1}^n (x_i - \bar{x})^2}{n-1}$$
where the sample standard deviation $s$ is the (positive) square root of the sample varaince.

The units of sample variance are the square of the original variable's units; the units of sample standard deviation is the original units of the variable itself. 

As expected, a small $s^2$ implies low variance; a high $s^2$ implies high variance in the data. Some various real-life examples include the commute time to work, the size of parts off an assembly line, and more.

The population variance for a population of $N$ values is
$$\sigma^2 = \frac{\sum_{i=1}^N (x_i - \bar{x})^2}{N}$$

that is, taking the average of the squares of the differences from the mean. You might notice that the sample variance/sample standard deviation divides by $n-1$ - this is because dividing by $n$ gives us an underapproximation.

We'll later find out how to estimate $\sigma^2$ from $s^2$.

Also, the sample range is simply the maximum over the sample minus the minimum.

## Section 6.3
We now move onto frequency distributions and histograms.

If we have a lot of data, it's typically a lot easier to analyze the data if we put it in terms of a frequency distribution, allowing us to see how the data is distributed.

In general, if you want to construct a histogram (which is the graphical representation of a frequency distribution):
- Calculate the square root of the observations - that's the number of bins you should use
- The bins must cover every value - that is, the bins must *at least* cover the range

For example, if we have 80 observations and a range of 169 units, we might take $\sqrt{80} = 9$ and use 9 bins, then find that we can use bin sizes of 20 to cover the whole range.

Note that each bin is *inclusive* at its lower bound, and *exclusive* at its upper bound. (This rule applies to the last bin, as well.)

Of course, it holds you can take frequency distribtuions and turn them into relative frequencies.