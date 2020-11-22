# Python Review

## Fundamental

### Language Type

Dynamic: the type of the data would be determined by the value you give to it

Weak: the type of the variable can be changed

Interpret: python interpreter can directly execute the code 

### Comment

#:pound sign

multiline :""" the python interpreter would read it but ignore it because it is not assigned to any variable

### Variables

Assign value to multiple variables

```python
x, y, z = "Orange", "Banana", "Cherry"
```

+

string+string

number+number

#### Local and Global

if you create a variable in a function with the same name of a global variable then the variable would be local in the function

you can use **global** to make it a global variable

### Data type

| Text Type:      | `str`                              |
| --------------- | ---------------------------------- |
| Numeric Types:  | `int`, `float`, `complex`          |
| Sequence Types: | `list`, `tuple`, `range`           |
| Mapping Type:   | `dict`                             |
| Set Types:      | `set`, `frozenset`                 |
| Boolean Type:   | `bool`                             |
| Binary Types:   | `bytes`, `bytearray`, `memoryview` |

#### dict:

hashtable but python use the open addressing 

 all entry records are stored in the bucket array itself. When a new entry has to be inserted, the buckets are examined, starting with the hashed-to slot and proceeding in some *probe sequence*, until an unoccupied slot is found. When searching for an entry, the buckets are scanned in the same sequence, until either the target record is found, or an unused array slot is found, which indicates that there is no such key in the table.

**important**: you cannot directly delete some records because if you delete it directly, there could be early stop when searching for a value

#### getting data type

type(x)

#### Set data type

datatype()

#### number

int

float

complex: 复数

You cannot convert complex numbers into another number type.

**random**: random.randrange(1,10)

#### String

you can use string as an arrays

##### slicing

##### negative indexing

##### len()

##### methods

strip()

lower()

upper()

replace()

split()

##### check string

"what" in str

##### format

"{}".format()

| \'   | Single Quote    | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_escape2) |
| ---- | --------------- | ------------------------------------------------------------ |
| \\   | Backslash       | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_backslash) |
| \n   | New Line        | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_newline) |
| \r   | Carriage Return | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_r) |
| \t   | Tab             | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_t) |
| \b   | Backspace       | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_b) |
| \f   | Form Feed       |                                                              |
| \ooo | Octal value     | [Try it »](https://www.w3schools.com/python/trypython.asp?filename=demo_string_octal) |
| \xhh | Hex value       |                                                              |

### Boolean

empty variable are false

One more value, or object in this case, evaluates to `False`, and that is if you have an object that is made from a class with a `__len__` function that returns `0` or `False`:

```python
class myclass():
 def __len__(self):
  return 0

myobj = myclass()
print(bool(myobj))
```

## Collections

- **List** is a collection which is ordered and changeable. Allows duplicate members.
- **Tuple** is a collection which is ordered and unchangeable. Allows duplicate members.
- **Set** is a collection which is unordered and unindexed. No duplicate members.
- **Dictionary** is a collection which is unordered, changeable and indexed. No duplicate members.

list is mutable

### List

in

len

append()

insert()

remove(item): item is one of the objects in the list

pop()

**del list[index]**

clear()

list.copy(): or list(): shallow copy

join: + extend(list2)

| [append()](https://www.w3schools.com/python/ref_list_append.asp) | Adds an element at the end of the list                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [clear()](https://www.w3schools.com/python/ref_list_clear.asp) | Removes all the elements from the list                       |
| [copy()](https://www.w3schools.com/python/ref_list_copy.asp) | Returns a copy of the list                                   |
| [count()](https://www.w3schools.com/python/ref_list_count.asp) | Returns the number of elements with the specified value      |
| [extend()](https://www.w3schools.com/python/ref_list_extend.asp) | Add the elements of a list (or any iterable), to the end of the current list |
| [index()](https://www.w3schools.com/python/ref_list_index.asp) | Returns the index of the first element with the specified value |
| [insert()](https://www.w3schools.com/python/ref_list_insert.asp) | Adds an element at the specified position                    |
| [pop()](https://www.w3schools.com/python/ref_list_pop.asp)   | Removes the element at the specified position                |
| [remove()](https://www.w3schools.com/python/ref_list_remove.asp) | Removes the item with the specified value                    |
| [reverse()](https://www.w3schools.com/python/ref_list_reverse.asp) | Reverses the order of the list                               |
| [sort()](https://www.w3schools.com/python/ref_list_sort.asp) | Sorts the list list.sort(reverse=, key=)                     |

### Tuple

join: +

constructor: tuple()

### Set

#### Access: 

You cannot access items in a set by referring to an index or a key.

```python
thisset = {"apple", "banana", "cherry"}

for x in thisset:
  print(x)
```

| Method                                                       | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [add()](https://www.w3schools.com/python/ref_set_add.asp)    | Adds an element to the set                                   |
| [clear()](https://www.w3schools.com/python/ref_set_clear.asp) | Removes all the elements from the set                        |
| [copy()](https://www.w3schools.com/python/ref_set_copy.asp)  | Returns a copy of the set                                    |
| [difference()](https://www.w3schools.com/python/ref_set_difference.asp) | Returns a set containing the difference between two or more sets |
| [difference_update()](https://www.w3schools.com/python/ref_set_difference_update.asp) | Removes the items in this set that are also included in another, specified set |
| [discard()](https://www.w3schools.com/python/ref_set_discard.asp) | Remove the specified item                                    |
| [intersection()](https://www.w3schools.com/python/ref_set_intersection.asp) | Returns a set, that is the intersection of two other sets    |
| [intersection_update()](https://www.w3schools.com/python/ref_set_intersection_update.asp) | Removes the items in this set that are not present in other, specified set(s) |
| [isdisjoint()](https://www.w3schools.com/python/ref_set_isdisjoint.asp) | Returns whether two sets have a intersection or not          |
| [issubset()](https://www.w3schools.com/python/ref_set_issubset.asp) | Returns whether another set contains this set or not         |
| [issuperset()](https://www.w3schools.com/python/ref_set_issuperset.asp) | Returns whether this set contains another set or not         |
| [pop()](https://www.w3schools.com/python/ref_set_pop.asp)    | Removes an element from the set                              |
| [remove()](https://www.w3schools.com/python/ref_set_remove.asp) | Removes the specified element                                |
| [symmetric_difference()](https://www.w3schools.com/python/ref_set_symmetric_difference.asp) | Returns a set with the symmetric differences of two sets     |
| [symmetric_difference_update()](https://www.w3schools.com/python/ref_set_symmetric_difference_update.asp) | inserts the symmetric differences from this set and another  |
| [union()](https://www.w3schools.com/python/ref_set_union.asp) | Return a set containing the union of sets                    |
| [update()](https://www.w3schools.com/python/ref_set_update.asp) | Update the set with the union of this set and others         |

### Dict

#### Access

use index

use get()

values()

items()

pop(key)

popitem():method removes the last inserted item (in versions before 3.7, a random item is removed instead)

del thisdict[key]

del thisdict

clear()

| Method                                                       | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [clear()](https://www.w3schools.com/python/ref_dictionary_clear.asp) | Removes all the elements from the dictionary                 |
| [copy()](https://www.w3schools.com/python/ref_dictionary_copy.asp) | Returns a copy of the dictionary                             |
| [fromkeys()](https://www.w3schools.com/python/ref_dictionary_fromkeys.asp) | Returns a dictionary with the specified keys and value       |
| [get()](https://www.w3schools.com/python/ref_dictionary_get.asp) | Returns the value of the specified key                       |
| [items()](https://www.w3schools.com/python/ref_dictionary_items.asp) | Returns a list containing a tuple for each key value pair    |
| [keys()](https://www.w3schools.com/python/ref_dictionary_keys.asp) | Returns a list containing the dictionary's keys              |
| [pop()](https://www.w3schools.com/python/ref_dictionary_pop.asp) | Removes the element with the specified key                   |
| [popitem()](https://www.w3schools.com/python/ref_dictionary_popitem.asp) | Removes the last inserted key-value pair                     |
| [setdefault()](https://www.w3schools.com/python/ref_dictionary_setdefault.asp) | Returns the value of the specified key. If the key does not exist: insert the key, with the specified value |
| [update()](https://www.w3schools.com/python/ref_dictionary_update.asp) | Updates the dictionary with the specified key-value pairs    |
| [values()](https://www.w3schools.com/python/ref_dictionary_values.asp) | Returns a list of all the values in the dictionary           |

## For loop

### Range

```python
for x in range(2, 30, 3):
  print(x)
```

## Functions

Arbitrary arguments: *args

arbitrary keyword arguments: **kwargs

## Lambda

```python
lambda arguments : expression
```

```python
x = lambda a : a + 10
print(x(5))
```

### why

Use lambda functions when an anonymous function is required for a short period of time.

## Classes and objects

The `self` parameter is a reference to the current instance of the class, and is used to access variables that belongs to the class.

```python
__init__()

```

### modify

```python
instance.attribute=value
del instance.attribute
del instance
```

### inheritance

```python
class Student(Person):
  def __init__(self, fname, lname):
    super().__init__(fname, lname)
```

## Iterator

An iterator is an object that contains a countable number of values.

An iterator is an object that can be iterated upon, meaning that you can traverse through all the values.

Technically, in Python, an iterator is an object which implements the iterator protocol, which consist of the methods `__iter__()` and `__next__()`.

Lists, tuples, dictionaries, and sets are all iterable objects. They are iterable *containers* which you can get an iterator from.

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self

  def __next__(self):
    x = self.a
    self.a += 1
    return x

myclass = MyNumbers()
myiter = iter(myclass)

print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
```

### StopIteration

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self

  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration

myclass = MyNumbers()
myiter = iter(myclass)

for x in myiter:
  print(x)
```

## Module

### dir

There is a built-in function to list all the function names (or variable names) in a module. The `dir()` function:

```python
import platform

x = dir(platform)
print(x)
```

## Dates

```python
import datetime

x = datetime.datetime.now()
print(x)
```

```python
import datetime

x = datetime.datetime(2020, 5, 17)

print(x)
```

## Math

### Built-in

min

max

abs

pow(x,y)

### Math module

## JSON

json.dumps(dict)

- | Python | JSON   |
  | :----- | :----- |
  | dict   | Object |
  | list   | Array  |
  | tuple  | Array  |
  | str    | String |
  | int    | Number |
  | float  | Number |
  | True   | true   |
  | False  | false  |
  | None   | null   |

## RegEx

re

| [findall](https://www.w3schools.com/python/python_regex.asp#findall) | Returns a list containing all matches                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [search](https://www.w3schools.com/python/python_regex.asp#search) | Returns a [Match object](https://www.w3schools.com/python/python_regex.asp#matchobject) if there is a match anywhere in the string |
| [split](https://www.w3schools.com/python/python_regex.asp#split) | Returns a list where the string has been split at each match |
| [sub](https://www.w3schools.com/python/python_regex.asp#sub) | Replaces one or many matches with a string                   |

### match object

The Match object has properties and methods used to retrieve information about the search, and the result:

`.span()` returns a tuple containing the start-, and end positions of the match.
`.string` returns the string passed into the function
`.group()` returns the part of the string where there was a match

## Try..Except

```python
try:
  print("Hello")
except:
  print("Something went wrong")
else:
  print("Nothing went wrong")

try:
  f = open("demofile.txt")
  f.write("Lorum Ipsum")
except:
  print("Something went wrong when writing to the file")
finally:
  f.close()

x = -1

if x < 0:
  raise Exception("Sorry, no numbers below zero")

x = "hello"

if not type(x) is int:
  raise TypeError("Only integers are allowed")
```

## Input

```python
username = input("Enter username:")
print("Username is: " + username)
```

