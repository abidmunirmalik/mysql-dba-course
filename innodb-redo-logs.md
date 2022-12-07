## INNODB REDO LOG FILES

### SET CLEAN SHUTDOWN
```sql
show global variables like 'innodb_fast_shutdown';
SET GLOBAL innodb_fast_shutdown = 0;
```

### SHUTDOWN MYSQL
```sh
sudo systemctl stop mysqld.service
```

### REMOVE REDO LOG FILES
```sh
sudo rm -f /var/lib/mysql/prod/ib_logfile*
```

### RESTART MYSQL  
```sh
sudo systemctl start mysqld.service
```

### VERIFY
```sh
sudo ls -l /var/lib/mysql/prod/
```

## RE-CONFIGURE REDO LOG FILES

### SET CLEAN SHUTDOWN 
```sql
show global variables like 'innodb_fast_shutdown';
SET GLOBAL innodb_fast_shutdown = 0;
```

### SHUTDOWN MYSQL
```sh
sudo systemctl stop mysqld.service
```

### REMOVE REDO LOG FILES
```sh
sudo rm -f /var/lib/mysql/prod/ib_logfile*
```

### CHANGE PERMISSIONS
```sh
sudo mkdir /var/log/mysql/redologs
sudo chown -R mysql:mysql /var/log/mysql
```

### CONFIGURE REDO LOG FILES
```sh
sudo vim /etc/percona/innodb.cnf
innodb-log-file-size = 100M
innodb-log-files-in-group = 2
innodb-log-group-home_dir = /var/log/mysql/redologs
```

### RESTART MYSQL  
```sh
sudo systemctl start mysqld.service
```

### VERIFY
```sql
SHOW GLOBAL VARIABLES LIKE 'innodb_log%'
```
