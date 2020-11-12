# 1 Recursion
## 1.1 Reduction
Reducing X to Y means to write an algorithm for X that uses an alogrithm for Y as a black box and subroutine.

## 1.2 Simplify and Delegate
Recursion is kind of reduction:
- If the given instance of the problem can be solved directly, solve it directly. 
- Otherwise,reduce it to one or more simpler instances of the same problem.

**Induction Hypothesis**:
- base case
- No infinite sequence of reductions to simpler and simpler instances

## 1.3 Tower of Hanoi
We want to move n disks from a source pge to a destination peg using a third temporary peg as a placeholder.

```
Hanoi(n,src,dst,tmp): 
	if n > 0 Hanoi(n−1,src,tmp,dst) 〈〈Recurse!〉〉
	move disk n from src to dst
	Hanoi(n−1,tmp,dst,src) 〈〈Recurse!〉〉
```

## 1.4 MergeSort
1. Divide to two array
2. Merge sort each array
3. Merge

```
MergeSort(A[1..n]): 
	if n > 1 m←bn/2c
		MergeSort(A[1..m]) 〈〈Recurse!〉〉
		MergeSort(A[m+1..n]) 〈〈Recurse!〉〉
		Merge(A[1..n],m)
		
Merge(A[1..n],m):
	i←1; 
	j←m+1 
	for k←1 to n 
		if j > n 
			B[k]←A[i]; i←i+1
		else if i > m 
			B[k]←A[j]; j← j+1
		else if A[i] < A[j] 
			B[k]←A[i]; i←i+1
		else B[k]←A[j]; j← j+1 
	for k←1 to n 
		A[k]←B[k]
```

## 1.5 QuickSort
Another recursive sorting algorithm
1. Choose a pivot element from the array
2. Partition the array into three subarrays containing the elements smaller than the pivot, the pivot itself and the elements larger than the pivot
3. Recursively quicksort the first and the last subarrays

```
QuickSort(A[1..n]): 
	if (n > 1) 
		Choose a pivot element A[p]
		r←Partition(A,p)
		QuickSort(A[1..r−1]) 〈〈Recurse!〉〉
		QuickSort(A[r +1..n]) 〈〈Recurse!〉〉


Partition(A[1..n],p): 
	swap A[p]↔A[n] 
	l←0 〈〈#items<pivot〉〉 
	for i←1 to n−1 
		if A[i] < A[n] 
			l←l+1 
			swap A[l]↔A[i]
		swap A[n]↔A[l+1]
	return l+1
```

## 1.6 The Pattern
**Divide and Conquer**:
1. Divide
2. Delegate
3. Combine

## 1.7 Recursion Tree



