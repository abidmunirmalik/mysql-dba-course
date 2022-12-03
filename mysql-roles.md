## CREATING MYSQL ROLES

### GET HELP
```sql
HELP CREATE ROLE
```

### CREATE READER, WRITER, ADMIN ROLES
```sql
CREATE ROLE IF NOT EXISTS READER, WRITER, ADMIN;
```

### GRANT PERMISSIONS TO ROLES
```sql
GRANT SELECT ON world.continents TO READER;
GRANT INSERT, UPDATE, DELETE ON world.continents TO WRITER;
GRANT ALL ON world.* TO ADMIN;
```

### CHECK ROLE PERMISSIONS
```sql
SHOW GRANTS FOR READER;
SHOW GRANTS FOR WRITER;
SHOW GRANTS FOR ADMIN;
```

### CREATE USERS
```sql
CREATE USER IF NOT EXISTS db_reader IDENTIFIED BY 'P@ssw0rd';
CREATE USER IF NOT EXISTS db_writer IDENTIFIED BY 'P@ssw0rd';
CREATE USER IF NOT EXISTS db_admin IDENTIFIED BY 'P@ssw0rd';
```

### GRANT ROLES TO USERS
```sql
GRANT READER TO db_reader;
GRANT WRITER to db_writer;
GRANT ADMIN to db_admin
```

### FLUSH PRIVILEGES  
```sql
FLUSH PRIVILEGES;
```