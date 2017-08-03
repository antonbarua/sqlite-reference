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

