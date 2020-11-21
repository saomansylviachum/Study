# File Handling

## open()

`"r"` - Read - Default value. Opens a file for reading, error if the file does not exist

`"a"` - Append - Opens a file for appending, creates the file if it does not exist

`"w"` - Write - Opens a file for writing, creates the file if it does not exist

`"x"` - Create - Creates the specified file, returns an error if the file exists

In addition you can specify if the file should be handled as binary or text mode

`"t"` - Text - Default value. Text mode

`"b"` - Binary - Binary mode (e.g. images)



## read

### read()

```python
f = open("D:\\myfiles\welcome.txt", "r")
print(f.read())
print(f.read(5))
```

### readline()

```python
f = open("demofile.txt", "r")
print(f.readline())
print(f.readline())
f.close()
```

## write

`"a"` - Append - will append to the end of the file

`"w"` - Write - will overwrite any existing content

## create

To create a new file in Python, use the `open()` method, with one of the following parameters:

`"x"` - Create - will create a file, returns an error if the file exist

`"a"` - Append - will create a file if the specified file does not exist

`"w"` - Write - will create a file if the specified file does not exist

```python
f = open("demofile2.txt", "a")
f.write("Now the file has more content!")
f.close()
f = open("myfile.txt", "x")
```

## delete

```python
import os
if os.path.exists("demofile.txt"):
  os.remove("demofile.txt")
else:
  print("The file does not exist")

import os
os.rmdir("myfolder")#only empty folder
```

