# EDA (Exploratory Data Analysis)
- Where to get data from?
	- open data gov: for datasets by governments that are publicly available
	- kaggle for public data
	- gather it yourself or through someone else locally
# Variable/Feature Types
## Categorical (qualitative):
- we take the frequency for measure, ex: the mode
- expressed as strings
- nominal:
	- no order/arrangement respective to other values of same feature
	- ex: country of birth, eye color
- ordinal:
	- there is order/arrangement
	- ex: small, medium, large
- binary:
	- is a yes or no
- Date/time:
	- we usually do transformation here, to extract only day or month or year
## Numerical (quantitative):
- we can take mean, median, measure the spread
- Discrete:
	- whole numbers
- Continuous:
	- ex: height/weight
# Objects and Attributes
- objects: these are records of the data set
- attributes: features/columns/
## Types of Attributes:
- Raw features:
	- ex: students id
- Derived features:
	- derived from raw features
	- may be:
		- aggregates
		- flags: 
			- may replace a feature with a flag
			- flag is a yes/no and put in place from a raw feature such as from the "year of joining" feature will be: "late" or "not late"
		- ratios:
			- can get rid of 2 features, and replace with 1 feature by taking their ratio
		- mappings:
			- may need to do mapping from categorical to numerical

>[!info] Advantage of Derived Features
>Derived features are useful to reduce the dimensionality of the dataset, as some models do not work with too many variables

# 3 Types of Data Exploration
- can do Summary statistics:
	- mean, median, measure spread (is data close to/far from mean) etc.
	- using pandas, can do:
```python
df[[columns]].agg(['mean', 'min', 'max'])
```
- or can do data visualization:
	- summary statistics can give good view, but still not enough
	- so visualization is extremely important, [see Anscombes Quartet](https://en.wikipedia.org/wiki/Anscombe%27s_quartet) for proof
	- can use this to get rid of outliers
	- challenge is to choose a suitable chart for the data
	- challenge is also how to 
	- categorical data: bar chart, pie chart
	- numerical data: 
		- histogram (can get rid of outliers from 3 times the standard deviation if we have normal distribution)
		- boxplot (can get rid of outlier using this by removing data that lay beyond the whiskers, the 3rd/1st quartile by IQR\*1.5) can do this by:
		```python
		df.clip(min, max)
		```

		- line plot: for time stamps, trends
- Univariate:
	- concentrate on 1 feature at a time by doing summary statistics or visualization
- Bivariate:
	- same, but with 2 features
	- types:
		- numerical vs numerical
		- categorical vs numerical
		- categorical vs categorical
	- will use scatterplot to visualize relationship/correlation between 2 variables
	- can do joint plot: combination between scatterplot and histogram
		- can see degree of correlation
			- we will use Pearson's correlation coefficient $$r=\frac{\Sigma()}{}$$
			- where we do sum  of product of differences, we do division to get a value between -1 and 1 (1 is linear relationship), this is its advantage, that data is linearly correlated, which is more information than Spearmans formula, 
			- pearsons correlation has assumptions for it to work:
				- correlation is linear
				- normally distributed
				- variables are independant of one another.
			- to remove the assumptions, we can use Spearman's Rank Correlation: $$\rho=1-\frac{6\Sigma d^2_i}{n(n^2-1)}$$
			- here we will take the data on x-axis, and rank it from highest to lowest of both features, and feed it to the formula, which uses difference of the 2 ranks: $d$ 
	- for categorical:
		- best is stacked bar plot
- Multivariate:
	- same with multiple features
