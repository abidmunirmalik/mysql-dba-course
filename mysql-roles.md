## CREATING MYSQL ROLES

### GET HELP
```sql
mysql>help create role
```

### CREATE READER, WRITER, ADMIN ROLES
```sql
mysql>CREATE ROLE IF NOT EXISTS READER, WRITER, ADMIN;
```

### GRANT PERMISSIONS TO ROLES
```sql
mysql>GRANT SELECT ON world.continents TO READER;
mysql>GRANT INSERT, UPDATE, DELETE ON world.continents TO WRITER;
mysql>GRANT ALL ON world.* TO ADMIN;
```

### CREATE USERS
```sql
mysql> CREATE USER db_reader IDENTIFIED BY 'P@ssw0rd';
mysql> CREATE USER db_writer IDENTIFIED BY 'P@ssw0rd';
mysql> CREATE USER db_admin IDENTIFIED BY 'P@ssw0rd';
```

### GRANT ROLES TO USERS
```sql
mysql>GRANT READER TO db_reader;
mysql>GRANT WRITER to db_writer;
mysql>GRANT ADMIN to db_admin
```

### FLUSH PRIVILEGES  
```sql
mysql>FLUSH PRIVILEGES;
```
