# Shell Script

## Read Command

read <varname>

read -p "statement" <varname>

## Command Subsitution

```sh
line=$(grep "beast" /examples/lionsInTheStreet)
echo $line
A beast caged in the heart of a city

```



## Condition Control

1. IF

   ```shell
   if [condition]
   then 
   	
   else
   	
   fi
   
   ```

   number

| Symbol | Meaning |
| ------ | ------- |
| -lt    | <       |
| -gt    | >       |
| -le    | <=      |
| -ge    | >=      |
| -eq    | ==      |
| -ne    | !=      |

string

| Symbol | Meaning         |
| ------ | --------------- |
| =      | equal           |
| !=     | not equal       |
| <      | less than       |
| >      | greater than    |
| -n s1  | s1 is not empty |
| -z s1  | s1 is empty     |

file

| Symbol            | Meaning                                  |
| ----------------- | ---------------------------------------- |
| -d directory name | returns true if directory exists         |
| -e filename       | returns true if file exists              |
| -f filename       | Check for file existence not a directory |
| -r filename       | Check if file is readable                |
| -s filename       | Check if file is of nonzero size         |
| -w filename       | Check if file is writable                |
| -x filename       | Check if file is executable              |

## Loop

1. for

   ·     for var in <range of values>

   ·     for ((   ;  ;  ))

   ·     for var in $(command)



## Function

function functionname()

{

}

### return value

function functionname()

{

echo $name

}

### variable scope

implicitly global

explictly local

## Arrays

```shell
#!/bin/bash

#Declare array with 4 elements
ARRAY=( 'A' 'B' 'C' 'D' )

# get the number of elements in the array
ELEMENTS=${#ARRAY[@]}

# display each element  
# for loop
for (( i=0;i<$ELEMENTS;i++))
do
    echo ${ARRAY[${i}]}
done


```

## Case

```sh
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

## getopts

getopts optstring name

shift [n]

shift $(($OPTIND-1))