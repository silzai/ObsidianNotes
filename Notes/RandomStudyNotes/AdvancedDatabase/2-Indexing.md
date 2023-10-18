## What is it?
- Is another auxiliary file built for the original file, that has pointers to the original file
- an Index file is always ordered
- Used to speed up retrieval of data
- Index files will be either sequential files, hash or a tree data structure
- A DBMS naturally creates index for the primary key in a table
- the size of an index file is always smaller than original file because it the number of records in the index file is same as number of blocks the file is divided into.
- A record in an index field has only 2 fields/columns, the primary index (primary key field of original file) and the block pointer
## We have different types of indexes:
- We have primary and clustering indexes, and secondary indexes.
- Have tree indexes (b+ trees), for trees, will read up to the height of the tree, so cost is $treeHeight + 1$, where adding 1 is cost of reading the data
- $bfr_i$ is the "fan-out" of the tree, and $fanOut=n$ , where n is the value that we divide the tree at each level (or dividing the search space).

## Good resources on indexes:
- [Indexes by montanaU](https://www.cs.montana.edu/courses/spring2004/435/lectures/IndexingFiles.html) (try clicking on the link)
- [Indexes by ucDavis](https://web.cs.ucdavis.edu/~green/courses/ecs165a-w11/7-indexes.pdf)
- the indexes image I sent