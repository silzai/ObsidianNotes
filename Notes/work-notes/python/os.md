# To traverse a directory recursively
```python
root_dir = "./dir"
for dir_, _, files in os.walk(root_dir):
	for file_name in files:
		rel_dir = os.path.relpath(dir_, root_dir)
		rel_file = os.path.join(root_dir, rel_dir, file_name)
# rel_file is the relative path of file with regards to root_dir
# but mabey this will not work for all directories, will need to check
```
