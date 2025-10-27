## Overview of Index Types

* [Main source](https://www.postgresql.org/docs/current/indexes-types.html)


### B-Tree
* The default index used
* It works on most primitive data types
* Can handle the  "<  <=  =  >=  >" operations
* Name is a bit misleading as it is not just a balanced tree, but a balanced tree with a double linked list at its base (more details later).


### Hash
* Store a 32-bit hash code derived from the value of the indexed column. Hence, such indexes can only handle simple equality comparisons.
* Its job can be done by the more versatile B-Tree index, but Hash indexes can be slightly faster for equality operations in some specific circumstances.

### GiST (Generalized Search Tree)
<div align="center">
  <img src="images/gist_spatial.png" width="800"/>
  <img src="images/gist_signatures.png" width="800"/>
</div>

* [A quick 8 minute introduction](https://www.youtube.com/watch?v=zw4-Hpm7ysk)
* Is a framework for building indexes on complex data types: spatial coordinates (pictured on the left), trees, text (for searching, pictured on the right using signatures which hint if a word *might* be present but do not 100% guarantee it due to collisions), etc.
* Some GiST indexes can be found [here](http://www.sai.msu.su/~megera/postgres/gist/)

### SP-GiST (Space-Partitioned GiST)

<center><img src="images/sp_gist_quadtree.png" width="800"/></center>

* SP-GiST supports partitioned search trees, which facilitate development of a wide range of different non-balanced data structures, such as quad-trees (pictured above), k-d trees, and radix trees (tries).
* The common feature of these structures is that they repeatedly divide the search space into partitions that need not be of equal size. Searches that are well matched to the partitioning rule can be very fast.