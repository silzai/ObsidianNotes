# Data Preprocessing
- We do it this to:
	- reduce training time
	- boost performance of algorithm
# 1) Data Cleaning:
# What to do with missing values (NA)?
- First of all Remove features that are missing in excess of 60% of their values, if not, then:
## If values are missing at random:
- we can only do this if data is missing at random, otherwise data distribution will be changed and no more than 5% data per variable is missing, otherwise will distort the distribution
- if data has normal distribution: 
	- will use mean
- if data is skewed: 
	- will use median
- if data is categorical: 
	- will use mode

## If data is missing on purpose:
- then we will actually do some research in the domain and replace the values with a reasonable arbitrary value.
## If nothing works, then:
- then replace the missing values with flags that will indicate that these are not applicable
# 2) Data Transformation:

## Feature Scaling:
- may need to fix magnitude as some ML algorithms are really sensitive to magnitude of values to each other
- will fix this with scaling, plus this will not change the shape of the distribution:
	- normalization 
		- also called min-max scaling, values will be between 0 and 1$$x=$$ 
	- standardization:
		- will take mean and standard deviation, values will be between -1 and 1 $$x=$$
## Discretization (binning):
- converting continuous value to discrete value
- there may be some loss of data
- will need to see how many intervals we need to create, and the width of those intervals, we have 2 techniques:
	- Equal-width discretization:
		- will do `cut` in 
	- Equal-frequency discretization:
		- will do `qcut` in pandas
# 3) Data Reduction
- Data aggregation:
	- 
- vertically by sampling from the dataset
- feature selection:
	- if two variables have very high correlation, then we can drop one of them
	- 