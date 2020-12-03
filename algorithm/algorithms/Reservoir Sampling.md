# Reservoir Sampling
cite:[yufei's ppt](http://www.cse.cuhk.edu.hk/~taoyf/course/5705f10/lec7.pdf)
## Definition
This algorithm takes a random sample set of the desired size in only one pass over the underlying dataset. This feature
makes the algorithm ideal for stream environments where every item can be processed only once.

## Reservoir
### Problem
Given a set S of items, compute a random sample set of size k
### Algorithm
```
algorithm reservoir(k, S)
/* take k random samples from the dataset S */
1. initialize an array samples of size k
2. for i = 1 to n = |S|
3.  o = the i-th item
4.  if i ≤ k then
5.    samples[i] = o
6.  else
7.    generate a random integer from 1 to i
8.    if x ≤ k then
9.     samples[i] = o
```
### Analysis
O(1)

### Proof
#### Equal likelihood
After n ≥ k items in S have been processed, each of those items is sampled with probability k/n.
![proof](images/proofreservoir.jpg)
