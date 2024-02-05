# EDA (Exploratory Data Analysis)
- Where to get data from?
	- open data gov: for datasets by governments that are publicly available
	- kaggle for public data
	- gather it yourself or through someone else locally
# Variable Types
- Categorical (qualitative):
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
- Numerical (quantitative):
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
>Derived features are useful to reduce the dimensionlaity of the dataset, as some models do not work with too many variables

# 2 Types of Data Exploration
- can do Summary statistics:
	- 
- or can do data visualization:
	- 