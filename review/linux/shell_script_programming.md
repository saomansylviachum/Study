# Shell Script
## 1 Begin
**Run a script file**
``bash file``
**Debug a script file** ``bash -x file``

## 2 Variable

```bash
name=value
```
You may use ``$`` to read the value of the variable
**Concatenating** ``greet=$word1” ”$word2``

### 2.1 Passing Arguments to a Script
using $1 $2
**Positional Parameters - variables**
$0	script name
$# 	number of command line parameters
$*	contains all command line parameters
$@	contains all command line arguments
**Other useful variables**
$?	exit status of the most recently executed command
$$ - Process ID of the shell
$! - process ID of the most recently executed background command

### 2.2 Interactive Script Using Read Command
```bash
read namevar
```
```bash
read -p "Enter varname:" nameVar
```

### 2.3 Command Substitution
Command substitution allows us to treat the output of a command as a value.(First get the value of the command and then replace the command line variable with the value)

```bash
line=$(grep "beast" /examples/lionsInTheStreet)
echo $line
> A beast caged in the heart of a city
```
### 2.4 Array

```bash
#!/bin/bash
names[0]="Bob"
names[1]="Julie"
names[2]="Andrew"
names[3]="Alice
or
names=("Bob" "Julie" "Andrew" "Alice")
```
when use:

```bash
echo ${names[0]}   #First value
echo ${names[3]}   #Fourth value
echo ${names[*]}   #All values
echo ${#names[*]}  #Number of values
```

### 2.5 Arithmetic

```bash
$((mathExpression))
$[mathExpression]
```

example:

```bash
echo $((4/2))
echo $[3+2*5]
result=$[3*5]
echo $result
```

## 3 Condition Scripting
### 3.1 if statement

```bash
if command
then
   code
elif
then
   code
else
   code
fi
```

#### 3.1.1 Test Expression

test expression

```bash
if test  5  –gt  3
 then echo  $?
fi
```
[expression]

```bash
if [ 5 –gt 3 ]
 then echo $?
fi
```
**File Test**
-e name	File name exists.
-d name	File name is a directory. 
-f name 	File name is a regular file.
-h name	File name is a symbolic link.
-r name	File name exists and is readable. 
-w name	File name exists and is writeable. 
-x name	File name exists and is executable. 
-s name	File name exists and has nonzero size.
**String Test**
s1 = s2	String s1 equals string s2 
s1 != s2	String s1 does not equal string s2
-z  s1	String s1 has zero length 
-n  s1	String s1 has nonzero length
**Numeric Test**
n1 –eq n2	Integer n1 and n2 are equal
n1 –ne n2	Integer n1 and n2 are not equal
n1 –lt n2	Integer n1 is less than n2
n1 –le n2	Integer n1 is less than or equal to n2
n1 –gt n2	Integer n1 is greater than n2
n1 –ge n2	Integer n1 is greater than or equal to n2

#### 3.1.2 Conditional Operators
```bash
[[ condition1 || condition2 ]]
[[ condition1 && condition2 ]]

[ condition1 ] || [ condition2 ]
[ condition1 ] && [ condition2 ]

[ condition1 –o condition2 ]
[ condition1 –a condition2 ]
```

### 3.2 case statement

```bash
case value in
   pattern1)
      code ;;
   pattern2)
      code ;;
   patternN)
      code ;;
   *)
      code ;;
esac 
```

## 4 Flow Control
for
while
until

### 4.1 for

```bash
for i in 1 2 3 4 5 6 7 8 9 10
do
	echo $i
done

for i in {1..10}

for ((i=1;i<=10;i++))
do
	echo $i
done

for i in $*
do
	echo $i
done

for file in $(ls)
do
	echo $file
done
```

### 4.2 while&until

```bash
while/until[condition]
do
	command
done
```

## 5 Functions

### 5.1 Definition

```bash
function functionName(){
   code
}

or

functionName(){
   code
}
```

### 5.2 passing arguments
same as the script passed arguments

``$1 $2``

### 5.3 return value
``echo value``

### 5.4 return code
To exit the function
``return 0``
**0 means success and other means fail**

### 5.5 Variable Scope
**Important:** Default is global and if you want to set it as a local variable, you need to add ``local`` keyword

## 6 Built-in Commands
You can use ``type`` to check if a command is a built-in command

### 6.1 getopts
``getopts optstring name [args]``

":" before the option string means silent error reporting

``getopts :asmd opt``

### 6.2 shift
``shift [n]``
usually use:
``shift $(($OPTIND - 1))``
