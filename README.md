# SQLite Reference

### Create Database

In the sqlite> prompt, type .open [dbname] to create a new database if it doesn't exist.
```sql
.open test1.db
```

### Attach a database to the existing connection

```sql
attach database "test1.db" as test1
```

### See all databases in the existing connection

```sql
.databases
```

### See all the tables in a database

```sql
.tables
```

### See the structure of a table

```sql
.schema Table1
```

### Exit SQLite

```sql
.exit
```

### Primary Key

* A column or a group of columns that can uniquely define a row in a table.
* A table can have ONE AND ONLY ONE primary key
* SQL Standard: Primary key cannot contain NULL values
* SQLite specific: row id -> auto assigned
* SQLite specific: cannot use alter table to add primary key

Example:
```sql
Create Table Person (
    id integer primary key,
    name text not null
);

Create Table Item (
    item_id integer,
    factory_id integer,
    primary key (item_id, factory_id)
);
``` 

### Foreign Key

A column (or a set of columns) in a table that refers to the primary key or a unique key in another table.

### Create Table

```sql
CREATE TABLE [IF NOT EXISTS] [SCHEMA].TABLE_NAME (
    COLUMN_NAME DATA_TYPE [PRIMARY KEY],
    COLUMN_NAME DATA_TYPE [NOT NULL],
    COLUMN_NAME DATA_TYPE [DEFAULT 0],
    COLUMN_NAME DATA_TYPE [UNIQUE]
    [CONSTRAINTS]
) [WITHOUT ROWID];
```

Examples:
```sql
CREATE TABLE Person (
    id integer primary key,
    name text not null
);

CREATE TABLE contact_area (
    contact_id integer not null,
    area_id integer not null,
    primary key(contact_id, area_id),
    foreign key(contact_id) references contacts (contact_id)
    on delete cascade on update no action,
    foreign key(area_id) references areas (area_id)
    on delete cascade on update no action
);
```
