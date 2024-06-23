# To initialize a dataframe using a dictionary
```python
# full name, email, department, faculty, University name
columns = [
	"full_name",
	"email",
	"department",
	"faculty",
	"university_name",
]

def initialize_df_from_template(dict):
	return pd.DataFrame(dict, columns=columns)
```
# to save dataframe as csv
```python
df.to_csv("output.csv", index = False, encoding="utf-8")
```
