## INNODB UNDO TABLESPACE

### SET CLEAN SHUTDOWN
```sql
show global variables like 'innodb_fast_shutdown';
SET GLOBAL innodb_fast_shutdown = 0;
```

### SHUTDOWN MYSQL
```sh
sudo systemctl stop mysqld.service
```

### RECONFIGURE innodb.cnf  
```sh
sudo mv /var/lib/mysql/prod/undo_* /var/lib/mysql/innodb/
sudo chown -R mysql:mysql /var/lib/mysql
sudo vim /etc/percona/innodb.cnf
innodb-undo-directory  =  /var/lib/mysql/innodb
```

### START MYSQL
```sh
sudo systemctl start mysqld.service
```

### VERIFY FILES
```sh
sudo ls -l /var/lib/mysql/innodb
```

### VERIFY SQL
```sql
SHOW GLOBAL VARIABLES LIKE 'innodb_undo%';
select * from information_schema.files where tablespace_name like '%undo%'\G
```
