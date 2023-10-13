**Resolve: Nausea example**

Our test statistic comes out to -2.33.

Since this is a two-sided test, if we use the P-value approach, we must take the sum of the area to the left of $z = -2.33$ plus the area to the right of $z = 2.33$.

The p-value is then 0.0198. But since $\alpha = 0.01$, and the p-value is less than the significance level, we fail to reject $H_0$. Therefore, there is no strong evidence for the alternative hypothesis in this case.

Simialrly, doing the critical region approach, we use the critical regions corresponding to $-z_{\alpha/2}$ and $z_{\alpha/2}$, which are the critical points corresponding to a left and right area of $\alpha/2 = 0.005$, respectively.

The corresponding critical values are $z = -2.58$ and $z = 2.58$. Since our test statistic lies within outside of the rejection region, we fail to reject $H_0$. In other words - this does not support $H_1$. 

## Section 11.1
This chapter addresses simple linear regressions, where our first section is on empirical models.

A deterministic (or mathematical) relationship indicates that the value of one variable can be reliably and accurately determined by the manipulation of the other variable. That is, you can find a formula in terms of one variable to describe the other variable.

But in many situations, the relationships between variables is not deterministic - that is, nondeterministic. For example, the electrical energy consumption is likely to be *related* to the size of a house, but equal-sized houses are not going to use *exactly* the same amount of energy.

The idea behind linear regressions is that we can approach nondeterminstic data with a deterministic relationship. 

One way to do this is through Lagrange interpolation - given a finite number of points for which no two points share the same $x$, it is always possible to find a polynomial that passes through all of them. If we then want to use this function to predict the value at some specific $x$ (for which there is not already a data point), we'll find that this is often not a great practical estimation.

What if, instead, we draw a line that more or less passes near all of the points that appear to exhibit a lienar trend? Then, we can use this line to describe the nondeterministic relationship. Of course, there will exist some nonzero error between the line and the various (known) points it is trying to represent.

The collection of statistical tools that are used to model and explore relationships between variables that are related in a nondeterministic manner is called regression analysis.

We focus on the situation in which there exists only one independent or predictor variable $x$ and the relationship with the response $y$ is assumed to be linear. (There are, of course, other regression methods, like polynomial regression.) Despite its simplicity, many practical problems fall into this framework.

We often use scatter plots to represent the data.

The mean of the random variable $Y$ is related to $x$ by the given following straight-line relationship:

$$\underbrace{E(Y|x)}_\text{Expected value of y given x} = 
\mu_{Y|x} = \beta_0 + \beta_1 * x$$

In other words, we can generate a line that describes the data with the formula $y = \beta_0+\beta_1*x$.

Notice that the formula entails $\mu_{Y|x}$. That is, the mean of $Y$ when $x$ is given. Our line, then, gives us an "average value" of sorts. The appropriate way to generalize this to a probalistic linear model is to assume that the expected value of $Y$ is a linear function fo $x$, though the actual value of $Y$ is determined by the mean value function plus a random error term.

$$Y = \beta_0 + \beta_1*x + \epsilon$$

The slope, $\beta_1$, can be interpreted as the change in the mean of $Y$ for a unit change in $x$. Then, $\beta_0$ is the y-intercept.

Another assumption is that $\epsilon$ is normally distributed with a mean of 0 and a variance of $\sigma^2$. Then, the variability of $Y$ at a particular value of $x$ is determined by the error variance $\sigma^2$. That is to say, $\sigma^2$ can be used to describe the variability in an estimate for $Y$ from a given $x$ value, where this variability is normally distributed.

When $\sigma^2$ is small, the observed (real/actual) values of $Y$ will fall close to the line; when $\sigma^2$ is large, the observed values of $Y$ may deviate considerably from the line. That is - the more vertically spread out the data is, the greater $\sigma^2$ is.

For example, suppose that the true regression model relating oxygenr purity to hydrocarbon level is $\mu_{Y|x} = 75+15x$, and suppose that the variance is $\sigma^2 = 2$. 

If $x = 1$, then what do we know? Plugging in the expression into the function, the exact point on the regression line is $(1, 90)$. Here, $\sigma \approx 1.4$, and since the distribution of variability is normal, this means that the actual value is likely (68%, by the empirical rule) to fall within one standard deivation of the expected value 90 - that is, there is a 68% likelihood the actual value lies between 88.6 and 91.4.

