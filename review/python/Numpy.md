# Numpy

numpy is a python library working with arrays.

- faster than list
- because it stores in an continuous storage

## arrays

### ndarray

- arr = np.array([1, 2, 3, 4], ndmin=5)

- check dimension: array.ndim

### accessing

arr[0,1]

### slicing

```python
print(arr[0:2, 1:4])
```

## Data type in numpy

- `i` - integer
- `b` - boolean
- `u` - unsigned integer
- `f` - float
- `c` - complex float
- `m` - timedelta
- `M` - datetime
- `O` - object
- `S` - string
- `U` - unicode string
- `V` - fixed chunk of memory for other type ( void )

### check

```python
arr.dtype
```

### convert

```python
arr.astype
```

## Copy and view

**copy**: new array, owns the data and any changes made to the copy will not affect the original array

```python
arr = np.array([1, 2, 3, 4, 5])
x = arr.copy()
```



**view**: 

The view *does not own* the data and any changes made to the view will affect the original array, and any changes made to the original array will affect the view

```view
arr = np.array([1, 2, 3, 4, 5])
x = arr.view()
arr[0] = 42
```

#### check if array owns it's data

x.base

## Shape

arr.shape

arr.reshape

**flattening**: arr.reshape(-1)

## Iterating

### typically

for i in arr

### nditer

```python
for x in np.nditer(arr):
  print(x)
for x in np.nditer(arr, flags=['buffered'], op_dtypes=['S']):
  print(x)#with different data types
for x in np.nditer(arr[:, ::2]):
  print(x)
```

### Enumerated iteration 

```python
for idx, x in np.ndenumerate(arr):
  print(idx, x)
"""

(0, 0) 1
(0, 1) 2
(0, 2) 3
(0, 3) 4
(1, 0) 5
(1, 1) 6
(1, 2) 7
(1, 3) 8
"""
```

## Join

in NumPy we join arrays by axes.

We pass a sequence of arrays that we want to join to the `concatenate()` function, along with the axis. If axis is not explicitly passed, it is taken as 0.

### concatenate

### stack

stacking is done along a new axis

![image-20201013214854044](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013214854044.png)

stack along rows

![image-20201013214954178](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013214954178.png)

along columns

![image-20201013215004862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013215004862.png)

height

![image-20201013215057351](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013215057351.png)

## Split

![image-20201013215311415](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013215311415.png)

## search

![image-20201013215341329](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013215341329.png)

![image-20201013215507037](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013215507037.png)

## sort

np.sort(arr)

## filter

```python
filter_arr = arr > 42

newarr = arr[filter_arr]
```

## random

````python
#Generate a random integer from 0 to 100:
x = random.randint(100)
#Generate a random float from 0 to 1:
x = random.rand()
x=random.randint(100, size=(5))
x = random.randint(100, size=(3, 5))


x = random.choice([3, 5, 7, 9])
x = random.choice([3, 5, 7, 9], size=(3, 5))
````

# ufunc

point to point operation

Create your own ufunc for addition:

```python
import numpy as np

def myadd(x, y):
 return x+y

myadd = np.frompyfunc(myadd, 2, 1)

print(myadd([1, 2, 3, 4], [5, 6, 7, 8]))
```

## summation

newarr = np.sum([arr1, arr2])

newarr = np.sum([arr1, arr2], axis=1)

newarr = np.cumsum(arr)# [1 3 6]

## difference

![image-20201013220504857](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013220504857.png)

## LCM(lowest common multiple/Greatest Common Denominator)

![image-20201013220633926](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013220633926.png)

![image-20201013220744669](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201013220744669.png)

## Trigonometric

```python
arr = np.array([np.pi/2, np.pi/3, np.pi/4, np.pi/5])

x = np.sin(arr)
x = np.deg2rad(arr)
x = np.rad2deg(arr)
x = np.arcsin(1.0)
x = np.hypot(base, perp)#勾股定理
```

