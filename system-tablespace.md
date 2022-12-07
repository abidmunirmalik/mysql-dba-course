## INNODB SYSTEM TABLESPACE

### SET CLEAN SHUTDOWN
```sql
show global variables like 'innodb_fast_shutdown';
SET GLOBAL innodb_fast_shutdown = 0;
```

### SHUTDOWN MYSQL
```sh
sudo systemctl stop mysqld.service
```

### CREATE DIRECTORY FOR SYSTEM TS DATA FILES
```sh
sudo mkdir /var/lib/mysql/innodb
sudo mv /var/lib/mysql/prod/ibdata1 /var/lib/mysql/innodb/
sudo chown -R mysql:mysql /var/lib/mysql
```

### RECONFIGURE innodb.cnf  
```sh
sudo vim /etc/percona/innodb.cnf
innodb-data-home-dir  =  /var/lib/mysql/innodb/
innodb-data-file-path = ibdata1:12M;ibdata2:10M:autoextend
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
```sh
SHOW GLOBAL VARIABLES LIKE 'innodb_data%';
SELECT * FROM INFORMATION_SCHEMA.FILES WHERE TABLESPACE_NAME LIKE 'innodb_system'\G
```

