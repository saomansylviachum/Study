# SQL 3

## Sub-queries

Using Subqueries containing aggregate functions

## Filtering Aggregation

Using having in group by

```sql
SELECT    broker_id
FROM      trades
WHERE     transaction_time > SYSDATE - 90
GROUP BY  broker_id
HAVING    AVG(share_amount) > 10000;

```

## Joining Tables 2

### Self join

### Cartesian join

```sql
SELECT 	b.broker_id, se.stock_ex_id
FROM   	brokers b CROSS JOIN stock_exchanges se;

```

## Correlated  Subquery

you want to find some columns with aggregation or other characteristics in seperated groups.

![image-20200926160655626](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200926160655626.png)



## View and inline-view

what is a view?

a view is a virtual table that allows you to access data from other tables and views.

A view contains no data itself therefore does not require additional storage

the tables upon which a view is based are called base table

a view is constructed using SELECT statement that involves one or more columns from one or more tables.

Once created view acts as a table and can be used accordingly in other commands.

![image-20200926161150546](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200926161150546.png)

### create

```sql
create or replace view <view name> as
<select statement>
```

### Drop

```sql
drop view <view name>
```



## Inline-View

From/temporary tables

What is cluster index and un-cluster index

