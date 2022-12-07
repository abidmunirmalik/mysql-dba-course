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
