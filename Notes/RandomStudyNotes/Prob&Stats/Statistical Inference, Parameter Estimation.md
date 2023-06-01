- Statistical Inference is divided into two major areas: 
	- parameter estimation
	- [[Statistical Inference, Hypothesis Testing]]
# Parameter Estimation:
- A statistic (mean etc.) that is gained from a sample of a population is called a ==**point estimate**== of that parameter/statistic.
- A statistic is also a random variable, so it has a probability distribution.
- The probability distribution of a statistic is called a ==sampling distribution==.
- $\theta$ will be used to represent any parameter, such as mean $\mu$ or variance $\sigma^2$ etc.
- The objective of point estimation is to select a single number, based on sample data, that is the most plausible value for $\theta$.
> A point estimate of some population parameter $\theta$ is a single numerical value $\hat{\theta}$ of a statistic $\hat{\Theta}$. The statistic $\hat{\Theta}$ is called the point estimator.

- We will make point estimates of the following parameters:
	1) The sample mean $\hat{\mu}$  
	2) The sample variance $\hat{\sigma^2}$  (or standard deviation $\hat{\sigma}$ ) 
	3) The sample proportion $\hat{p}$  of items in a population, $x/n$ , where $x$ is the number of items in a random sample of size $n$
	4) The difference in sample means of two populations, $\hat{\mu}_1-\hat{\mu_2}$
	5) The difference in two population sample proportions, $\hat{p}_1-\hat{p}_2$

> Central Limit Theorem:
> If $X_1, X_2,... X_n$ is a random sample of size $n$ taken from a population with mean $\mu$ and finite variance $\sigma^2$ , and if $\bar{X}$ is the sample mean, the form of the distribution of
> $$Z = \frac{\bar{X}-\mu}{\sigma/\sqrt{n}}$$
> as $n \to\infty$, , is the standard normal distribution.

## Example 1:
An electronics company manufactures resistors that have a mean resistance $\mu$ of 100 ohms and a standard deviation $\sigma$ of 10 ohms. The distribution of resistance is normal. Find the probability that a random sample of n = 25 resistors will have an average resistance $\bar{X}$ less than 95 ohms.
	Solution:
	The distribution is normal, and since because *linear functions of independent, normally distributed random variables are also normally distributed* so the sample mean will be:
	$\mu_{\bar{X}} = \mu$, so $\mu_{\bar{X}}=100$ and
	$\sigma_{\bar{X}} = \frac{\sigma}{\sqrt{n}}$, so $\sigma_{\bar{X}}=\frac{10}{\sqrt{25}}=2$ 
	After finding sample mean and sample standard deviation, we will solve normally by standardizing $\bar{X}$ = 95 using these statistics and finding the value using Z-table.

- Regarding the difference in sample means of two populations, $\hat{\mu}_1-\hat{\mu_2}$, the mean will be equal to the difference of the means of the population: be: $\mu_{\bar{X}_1-\bar{X}_2}$ =$\mu_{\bar{X}_1}-\mu_{\bar{X}_2}$= $\mu_1-\mu_2$ AND standard deviation will be same but SUMMED instead of subtracted.

