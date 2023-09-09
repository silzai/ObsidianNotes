- Used to speed up retrieval of data
- Is another auxiliary file built for the original file, that has pointers to the original file
- Index is always ordered
- Index files will be either sequential files, hash or a tree data structure
- A DBMS naturally creates index for the primary key in a table

- the size of an index file is always smaller than original file because it the number of records in the index file is same as number of blocks the file is divided into.
- A record in an index field has only 2 fields, the primary index (primary key field of original file) and the block pointer

- [Indexes by montanaU](https://www.cs.montana.edu/courses/spring2004/435/lectures/IndexingFiles.html) 
- [Indexes by ucDavis](https://web.cs.ucdavis.edu/~green/courses/ecs165a-w11/7-indexes.pdf)