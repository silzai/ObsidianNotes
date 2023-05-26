# What is an Index?
- When we have a huge amount of records (100,000 etc), then we it is very slow
- Oracle has DB optimizer (engine) 
- this engine does a "full table scan" on a query, takes a very long time, like searching for a word in a book
- instead of searching like that, we can just go to the end of the book, and look at the index of the book
- Oracle by default will put an "index" on a primary key
- but sometimes we do not query/search using the primary key, so in this case we need an index for the rest of the attributes as well, for ex, an index for first name
- so we have a table with 2 columns, 1st column is called the search key, 2nd column is for the attribute value, these 2 columns combined will create a single index
- advantages:
	- reduces query time
	- reduces the number of times we access the DV
	- improve performance
- when to put index? put one on an attribute that is used frequently

# Creating and using an Index
- create an index for an attribute, convention for naming is the index is tableName_attributeName_I:
```PLSQL
CREATE INDEX index_name
ON table_name(attribute_name);
```
- so after making the index like this, we can forget about it, and select normally, and the Oracle DB optimizer engine will use the index itself.
- When dropping tables, indexes are automatically dropped or can drop them individually.