# Isolation level
## Problem
1. Dirty read(caused by rollback)
2. Unrepeatable read: time1!=time2
3. Phantom read: other transaction insert

## Isolation level
1. read uncommited
2. read commited
3. repeatable read
4. serializable

# Index
Indexes is a mechanism that improve the speed of querying in the database.there are two types:
- Cluster indexes. in cluster index, the data row sorted in the order of the index order. There is only one cluster index in the database because there can be only one order in the databse.
- uncluster indexes: it would store the uncluster indexes in an seperate place int he disk. and each entry is key-value pair, when we can search the entry using key and the value would point to the position that the data places.



