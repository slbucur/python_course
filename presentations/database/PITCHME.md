## Databases in Python
### Introduction to Python @Cegeka

---

## Introduction

- Hands on training
- We will work with **SQLite** and **PostgreSQL**

---

## SQLite

- Useful database for single-user applications, think Desktop/mobile applications
- A single file contains the entire database
- Can be used as a data format
- Can be used entirely in memory
- Available by default in python


---

## SQLite basics

- SQLite __mostly__ follows the SQL standard
- It can't run on it's own, it needs to be run from a host program (ex. Python)

---

## Creating a table

```sql
CREATE TABLE animal(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT not null,
    race TEXT not null,
    quote TEXT
);
```

---

## Inserting into a table

```sql
INSERT INTO animal(name, race, emoji) VALUES ('panda', 'mammal', 'pandas like lavandas'), ('iguana', 'lizard', 'iguana likes your momma');
```

---

## Selecting data

```sql
SELECT * FROM animal;
```

---

## Update

```sql
UPDATE animal SET quote = 'iguana meets Joanna' where name='iguana';
```

---

## DELETE

```sql
DELETE FROM animal where name='panda';
```

---


## Using SQLite in python

- available as standard module
- **sqlite3**

```python
import sqlite3

# first we establish a connection
connection = sqlite3.connect('test.db')

# then we need a cursor
cursor = connection.cursor()

# for CREATE/INSERT/UPDATE/DELETE
# only execute is enough
cursor.execute("""
    CREATE TABLE animal(
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT not null,
        race TEXT not null,
        quote TEXT
    );
""")

# for SELECT
# first execute
cursor.execute("SELECT * FROM sqlite_master")

# then fetch
cursor.fetchall()
```