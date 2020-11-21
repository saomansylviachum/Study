# SQL

## DDL

UNIQUE: A column in a table which consists of unique values. can contain NULL value

## DML

```sql
insert into places(
place_id, city, country) 
values(
1,'London','UK'
);

update places
set country = 'United Kingdom' 
where country = 'UK';

DELETE FROM places
WHERE	country = 'UK';

```

##### ROLLBACK: undo changes you have not committed using it to your last COMMIT

### Wildcards

%

_

### Join

```SQL
SELECT
	brokers.first_name,
	brokers.last_name,
	NVL(trades.price_total,0)
FROM
	brokers
LEFT OUTER JOIN
	trades
ON
	brokers.broker_id = trades.broker_id
;
```

### DISTINCT