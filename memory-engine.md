## MYSQL MEMORY STORAGE ENGINE DEMO

### CREATE TABLE IN MEMORY STORAGE ENGINE
```sql
use world;
CREATE TABLE continents ( cid int NOT NULL, cname VARCHAR(25) NOT NULL) ENGINE=MEMORY;
SELECT * FROM continents;
```

### INSERT DATA INTO MEMORY TABLE
```sql
INSERT INTO continents(cid,cname) 
VALUES
 (1,'Asia'),
 (2,'Africa'),
 (3,'Europe'),
 (4,'North America'),
 (5,'South America'),
 (6,'Australia'),
 (7,'Antarctica');
```

### GET TABLE INFORMATION FROM INFORMATION_SCHEMA
```sql
SELECT TABLE_NAME,TABLE_TYPE,ENGINE,TABLE_ROWS,CREATE_TIME FROM INFORMATION_SCHEMA.TABLES WHERE ENGINE='MEMORY';
```

### RESTART MYSQL SERVICE
```sh
sudo systemctl stop mysqld && sudo systemctl start mysqld
```

### OBSERVE THE MEMORY TABLE
```sql
use world;
show tables;
SELECT * FROM continents;
```
