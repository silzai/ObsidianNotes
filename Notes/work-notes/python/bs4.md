# To import
```python
from bs4 import BeautifulSoup
with open("index.html", "r", encoding="utf-8") as f:
	doc = BeautifulSoup(f, "html.parser")
```
# get first instance of a tag
```python
# here we are getting the first p tag
tag = doc.find("p")
```
# get all instances of a tag
```python
# here we are getting the first p tag
tag = doc.find_all("p")
# this will return a list
```
# find using class attribute
```python
tag = doc.find("div", class_="this-class")
```
# get all children as a list
```python
children_tags = parent_tag.contents 
```
