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



