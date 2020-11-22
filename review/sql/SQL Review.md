# SQL Review

## 1 Date Modeling

### 1.1 SQL

Includes DCL(control) DDL(definition) DML(Manipulation)

### 1.2 DBA 

Security(access privileges and recovery)

Maintenance(space performance backup)

### 1.3 Vendor

Provide services of the database

RDMS: Relational database modeling

### 1.4 Basic Terminology

#### Table

- Each table represents an entity

- Column: attribute
- row: instance

#### ERD

one to one

one to many 

one to zero or one

one to zero or many

**many to many**: split into three table and k3pp

### 1.5 Data Type

String VARCHAR(length)

Numeric NUMBER(Precision,Scale)

Date DATE

### 1.6 Normalization

Guarantee that a database is optimally structured

Prevent unnecessary duplication of data.

**First Normalization**: 

- No two duplicate rows
- Atomic values: Each row should only contain one value per column
- no repeated columns

**Second Normalization**: 

- The second & third normal forms ensure that a table only contains columns which are attributes of the entity the table represents
- §Columns which are not part of a compound primary key must be dependent on the whole of the compound primary key and not just part of it

**Third Normalization**: 

- §All non-key columns are not dependent on other non-key columns

## 2 Basic DDL
```sql
ALTER USER user_name IDENTIFIED BY new_password;
CREATE TABLE tablename(
  col_name DATA_TYPE PRIMARY KEY
)
```
### Constraints
PRIMARY KEY
FOREIGN KEY
UNIQUE
NOT NULL

```sql
CREATE TABLE tablename(
  col_name DATA_TYPE PRIMARY KEY
  col2 DATA_TYPE,
  CONSTRAINT constrain_name
  FOREIGN KEY(col2)
  REFERENCES foreigntable(othercol),
  CONSTRAINT constraint_name
  PRIMARY KEY(col1,col2)# this is optional choice
  
 )
```
### OTHER
```sql
DESC table_name;
DROP TABLE table_name;
DROP TABLE table_name CASCADE CONSTRAINTS;# when you have foreign key constraints in this table
```

## 3 DML
### 3.1 SELECT and FILTERING
#### 3.1.1 WHERE
##### Comparison
= > >= < <= <> !=
##### Logical Operators
IN
BETWEEN AND
IS NULL
LIKE
##### Boolean Operators
AND
OR
NOT (remember: IS NOT NULL)

#### 3.1.2 ORDER BY
Syntax
```sql
ORDER BY col_name ASC/DESC
```
#### 3.1.3 Wildcards
%
_

#### 3.1.4 Date data type
7 bytes: century,year,month,day,hour,minute,second

##### TO_CHAR
```sql
TO_CHAR(SYSDATE,'CC DAY DD/MM/YYYY HH:MI:SS')
```
##### Filter Date
```sql
SELECT ...
FROM ...
WHERE TO_CHAR(transaction_time,'YYMM')=TO_CHAR(SYSDATE,'YYMM')

...
WHERE TO_CHAR(...)=TO_CHAR(ADD_MONTHS(SYSDATE,-1),'YYMM')
TO_CHAR(...,'YYQ')
```

### 3.2 JOIN
Joins use an identified common column to obtain data from multiple tables using one query

INNER JOIN
OUTER JOIN(FULL RIGHT LEFT)

> what is left/right outer join
  return everything from the first/second table mentioned, and any corresponding data from the second/first table.
#### Self joiin
```sql
SELECT ...
from 
  table1 t1
inner join table1 t2
on t1.id=t2.id;
```
#### Cartesian Join
```sql
SELECT b.broker_id,se.stock_ex_id
FROM brokers b CROSS JOIN stock_exchanges se;
```
#### 3.2.1 Aliases
As
#### 3.2.2 Distinct
``select distinct ..``

### 3.3 Sub queries
```
where in/=subqueries
```


### 3.4 Set Functions
Combine the results of 2 or more queries

UNION
UNION ALL (duplicate are not removed)
INTERSECT
MINUS

### 3.5 Aggregation
COUNT
SUM
AVG
MIN
MAX

**when using the group by, you cannot directly use the alias**

#### Having
filter the result(even u didn't mention in the select)

## 4 Correlated Subqueries
We want to add a third column to our aggregation result you should add a correlated subquery

```sql
SELECT
  t.share_id,
  t.price_total,
  t.trade_id
FROM
  trades t
WHERE
 t.price_total=(
  SELECT
    MAX(t2.price_total)
  FROM
    trades t2
  WHERE
    t2.share_id=t.share_id
 )
;
```

## 5 views
The view is a virtual table that allows you to access data from other tables and views.
A view contains no data itself and therefore does not require additional storage

```sql
CREATE OR REPLACE VIEW <view_name> AS
<SELECT SQL_statement>;
```
### In-line-view
from (...)
