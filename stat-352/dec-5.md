Remember last time how we said we could describe a set of data using

$$Y = \beta_0 + \beta_1*x + \epsilon$$

where $\epsilon$ was some normally distributed random error term for any given estimate. How do we actually find the line itself, though?

One way is through least-squares estimation. 

We can express the $n$ observations in the sample as 
$$y_i = \beta_0 + \beta_1x_i + \epsilon_i$$
for $i = 1, 2, \ldots, n$.

The sum of the squares of the deviations of the observations from the true regression line is

$$L = \sum_{i=1}^{n}\epsilon_i^2 = \sum_{i=1}^{n}(y_i-\beta_0-\beta_1x_i)$$

If our goal is to minimize $L$, then:
$$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1\bar{x}$$
$$\hat{\beta}_1 = \frac{\sum\limits_{i=1}^{n}y_ix_i-\frac{\left(\sum\limits_{i=1}^n y_i\right)\left(\sum\limits_{i=1}^n x_i\right)}{n}}{\sum\limits_{i=1}^nx_i^2-\frac{\left(\sum\limits_{i=1}^{n}x_i\right)^2}{n}}$$

where $\bar{y} = \frac{1}{n}\sum\limits_{i=1}^n y_i$ and $\bar{x} = \frac{1}{n}\sum_\limits{i=1}^{n}x_i$.

Then, the fitted/estimated regression line is $\hat{y} = \hat{\beta}_0 + \hat{\beta}_1x$, where each pair of observations satisfies
$$y_i = \hat{\beta}_0 + \hat{\beta}_1 x_i + e_i$$
where $e_i = y_i - \hat{y}_i$ is called the residual.

Now, obviously $\hat{\beta}_1$ is not very easy to calcualte by hand. So instead, we introduce some new notation that will help make the calculations easier:

$$S_{xx}=\sum_{i=1}^n(x_i-\bar{x})^2=\sum_{i=1}^n x_i^2 - \frac{\left(\sum\limits_{i=1}^nx_i\right)^2}{n}$$
$$S_{xy} = \sum_{i=1}^n(y_i-\bar{y})(x_i-\bar{x}) = \sum_{i=1}^{n}x_iy_i- \frac{\left(\sum\limits_{i=1}^n y_i\right)\left(\sum\limits_{i=1}^n x_i\right)}{n}$$

so that
$$\hat{\beta}_1 = \frac{S_{xy}}{S_{xx}}$$

Often, parts of these expressions (like the summations) will be given, such that you are expected to substitute parts of the expressions in yourself.

---

For example, in the slides, suppose that we find that $\hat{\beta}_0 = 74.283$ and $\hat{\beta}_1 = 14.947$. Then, we find that

$$\hat{y} = 74.283 + 14.947x$$
The interpretation, then, is that using the regerssion model, we would predict oxygen purity of $\bar{y} = 89.23\%$ when the hydrocarbon level is $x = 1.00\%$. The 89.23% purity may be interpreted as an estimate of the true population mean purity when $x = 1.00\%$, or as an estimate of a new observation when $x = 1.00\%$. 

The regression model can also be used to predict new or future observations $Y$; that is, plugging in $x_0$ to the regression model gives us a point estimate of the response $Y_0$. 

However, notice that there is still another unknown parameter in our regression model  - the variance of the error term $\epsilon$, $\sigma^2$. The residuals $e_i = y_i - \hat{y_i}$ are used to obtain an estimate of $\sigma^2$. 

The sum of squares of the residuals is simply
$$SS_{E} = \sum_{i=1}^n e_i^2 = \sum_{i=1}^n(y_i-\hat{y}_i)^2$$
or, alternatively,
$$SS_E=SS_T-\hat{\beta}_1S_{xy}$$

An unbiased estimator of $\sigma^2$ is
$$\hat{\sigma}^2 = \frac{SS_E}{n-2}=\frac{SS_{T}-\hat{\beta}_1S_{xy}}{n-2}$$
where 
$$SS_T= \sum_{i=1}^n(y_i-\bar{y})^2 =\sum_{i=1}^{n}(y_i^2) - n\bar{y}^2$$

