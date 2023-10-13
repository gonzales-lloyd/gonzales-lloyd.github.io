## Section 6.3
A histogram is a visual display of the frequency distribution.  In general, the process for constructing a histogram is:
- Label the bin boundaries on the horizontal scale
- Mark and label the vertical scale with either the frequencies or the relative frequencies 
- Draw a rectangle above each bin where the height corresponds to that bin

It is worth noting that histograms can be sensitive to the number of bins and their width – for small data sets (or really wide bins), histograms may change dramatically in appearance if we change the number or width of bins.  Histograms are more stable and reliable for larger data sets, preferably of size 75+.

When the sample size is large, the histogram can provide a reasonably reliable indicator of the general shape of the distribution or pollution of measurements from which the sample was drawn.  

![[Pasted image 20221026132049.png]]

Where $\tilde{x}$ (the median, x-tilde) and $\bar{x}$ (the mean, x-bar) are relative to each other can tell us whether there exists a left or right skew (or bias) as shown above. Usually, the existence of "tails" is enough to intuitively see biases.

## Section 7.1
Here, we talk about point estimation.  

Statistical methods are used to make decisions and draw conclusions about population.  This specific approach to statistics is generally known as statistical inference, where we use techniques to utilize the information in a sample to draw conclusions about the population.  

Statistical inference may be divided into two areas: parameter estimation and hypothesis testing.  

A **parameter** is some numerical measurement describing some characteristic of a population.  This includes the population mean, the population variance, and so on. 

A **statistic** is a numerical measurement describing some characteristic of a sample, such as the sample mean and sample variance.  

In practice, we use sample data to compute some specific value that is a reasonable guess of the true population parameter.  This value is known as a **point estimate**.

**All statistics are random variables.** For example, the sample mean and sample variance are random variables because they'll vary as we perform random sampling.  But obviously some values of the sample mean and variance are more likely (or possible) than other values – this implies that there exists some distribution of the sample mean and sample variance, which are both random variables.  

We call the probability distribution of a statistic a **sampling distribution.**

The statistic we use to generate a point estimate of some population parameter is called the **point estimator.**

We often need to estimate the mean $\mu$ and variance $\sigma^2$ of populations, as well as the proportion $p$ of items in a population of interest.  Reasonable point estimates of each of these are expressed as:
- $\hat{\mu} = \bar{x}$, the sample mean
- $\hat{\sigma}^2 = s^2$, the sample variance
- $\hat{p} = x/n$, where $x$ is the number of items in the class of interest out of a random sample of size $n$

## Section 7.2
A random sample is where a sample of $n$ subjects is selected in such a way that every possible sample of the same size $n$ has the same chance of being chosen. 

Statistical inference is concerned with making decisions about a population based on the information contained in a random sample from that population.  The assumption of random samples is extremely important – if the sample is not random and is based on judgment or is flawed in some other way, statistical methods will not work properly and will lead to incorrect conclusions and decisions.  

The probability distribution of a statistic is called a **sampling distribution**. the sampling distribution of a statistic depends on the distribution of the population, the size of the sample, and the method of sample selection.  The probability distribution of  $\bar{X}$, for example, is called the sampling distribution of the mean.  

To construct a sampling distribution of the sample mean:
- First, consider all possible samples from the population with the same number of values in each simple; that is, $n$ is fixed.  
- Take the mean of each sample.  
- Construct a frequency distribution from means of these samples.  This distribution is called sampling distribution of the sample mean.  

> [!tip] The central limit theorem
> The central limit theorem states that if $X_1, X_2, \ldots, X_n$ is a random sample of size $n$ taken from a population with mean $\mu$ and finite variance $\sigma^2$ and if $\bar{X}$ is the sample mean, the distribution of
>  $$Z = \frac{\bar{X}-\mu}{\sigma/\sqrt{n}}$$
>  is the standard normal distribution, where the mean of the sampling distribution of the sample mean is $\sigma_{\bar{x}} = \sigma/\sqrt{n}$.

The normal approximation for $\bar{X}$ depends on the sample size $n$. ![[Pasted image 20221031101716.png]]

The central limit theorem can be assumed to apply under two cases:
- If the underlying distribution is symmetric and unimodal (not too far from normal), the central limit theorem will apply for small values of $n$, like 4 or 5.  
- If the sampled population is very nonnormal, larger samples will be required; generally, for $n \gt 30$, the central limit theorem will almost always apply.  

