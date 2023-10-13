**Final exam will be from sections 6.1 onwards, with greatest weight on 9.1 onwards.**

Tables III and IV will be provided; graphing calculator allowed; one-page, two-sided formula sheet allowed.

> [!example] Question 1

$H_0: \mu = 300$, $H_1: \mu \neq 300$, $\alpha = 0.05$, $n = 50$, $\sigma = 20$, $\bar{X} = 295$

then $Z_0 \approx -0.3867$, which is less than the two-sided critical value 1.96 and has a p-value 0.699, which is greater than $\alpha$.

Fail to reject $H_0$. There is no strong evidence for the alternative hypothesis.

> [!example] Question 2

take
$$\text{p-value} =\text{normCdf}\left(-\infty, \frac{0.47-0.5}{0.11/\sqrt{45}}, 0, 1\right)\approx 0.0336$$
>[!warning] Don't forget to take off the `*2` from the last question!


> [!example] Question 3

- $H_0: \sigma = 0.01$
- $H_1 : \sigma \gt 0.01$
- n = 15
- s = 0.009
- alpha = 0.01

test statistic is 11.34

one-sided, right-tailed test: use $\chi^2_{0.01, 14}$, which is `invchi^2(0.99, 14)`: this gives 29.141 as the critical point

since the test statistic is not within the rejection region, fail to reject $H_0$

> [!example] Question 4

since two-sided and $\hat{p}$ is less than $p_0$, take

$$\text{p-value} = \text{normcdf}(-\infty, \frac{0.85-0.90}{\sqrt{\frac{0.9(0.1)}{1000}}}, 0, 1)*2 \approx 1.363\times10^{-7}$$
> [!example] Question 4

Applying the formulas gives a slope of -2.33 and an intercept of 48.013.

Then our line is $y = 48.01 - 2.33x$; plug in any value to find the predicted value.

For example, at x=3.7, we predict 39.39; if the observed is 46.1, then our residual is 6.71.


> [!example] Question 5

If you are given a table of $x$ and $y$ values, the best approach is to calculate $x^2$, $y^2$, and $x*y$ for each observation. Then, take the column sum of $x$, $y$, $x^2$, $y^2$, and $x*y$. This, along with $n$, is sufficient to determine the slope and intercept.

From there, you can use formulas to do things like find the residuals and find variance.

> [!example] Question 6

Under CLT, the standard deviation of samples of $n=6$ is $3.5/\sqrt{6}$. If we want to find the probability that a mean sample tensile strength exceeds 75.75, we normalize it:

$$z_0=\frac{75.75-75.5}{3.5/\sqrt{6}} = 0.17$$

and take the area to its right (since we want to know the probability of exceeding this sample mean), using `normcdf(z0, infinity, 0, 1).` This gives us 0.43055, the probability. 

> [!example] Question 7

Simply use

> [!tip] Two-sided confidence interval for $\mu$
> $$\bar{x} - z_{\alpha/2} *\frac{\sigma}{\sqrt{n}}\leq \mu \leq \bar{x} + z_{\alpha/2}*\frac{\sigma}{\sqrt{n}}$$

![[Pasted image 20221102191852.png]]

Our critical value here is 1.96.  At this point, simply plug your values in.

> [!example] Question 8

Note that

> [!tip] Confidence interval for $\sigma^2$
> Then we may write 
> $$P(\chi^2_{1-\alpha/2, n-1} \leq X^2 \leq \chi^2_{\alpha/2, n-1}) = 1 - \alpha$$
> which amounts to constructing a confidence interval for the variance.
> 
> If $s^2$ is the sample variance from a random sample of $n$ observations from a normal distribution with unknown variance $\sigma^2$, then a $100(1-\alpha)$% confidence interval on $\sigma^2$ is
> $$\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}} \leq \sigma^2 \leq \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}$$

Plug in your values, using Table IV for the percentage points of $\chi^2$ (after subtracting one from $n$ for the degrees of freedom) or $\text{inv}\chi^2$ after converting the percentage points (right area) to the left area.

Note that since we need to find a confidence interval for $\sigma$ - not $\sigma^2$ - we must take the square root.

> [!example] Question 9

Use
> [!tip] Two-sided confidence interval for population proportion
> $$P\left(\hat{p} -z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \leq p \leq \hat{p}+z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \right)\approx 1-\alpha$$

Since this is a two-sided CI, and $\alpha = 0.05$, use the critical value 1.96.

The sample proportion is 0.68, and $n = 2500$. At this point, simply plug in numbers from there.


