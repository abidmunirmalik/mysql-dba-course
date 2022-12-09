## PERFORMING COLD MYSQL BACKUP

### GET FILES PATHS
```sql
SHOW GLOBAL VARIABLES LIKE 'datadir';
SHOW GLOBAL VARIABLES LIKE 'innodb_data%';
sudo vim /etc/mysql/my.cnf
```

### SET CLEAN SHUTDOWN
```sql
show global variables like 'innodb_fast_shutdown';
SET GLOBAL innodb_fast_shutdown = 0;
```

### SHUTDOWN MYSQL
```sh
sudo systemctl stop mysqld.service
```

### COPY FILES  
```sh
sudo mkdir /tmp/coldbackup
sudo cp -r /var/lib/mysql/prod /tmp/coldbackup/
sudo cp -r /var/lib/mysql/innodb /tmp/coldbackup/
sudo cp /etc/percona/*.cnf /tmp/coldbackup/
```

### START MYSQL
```sh
sudo systemctl start mysqld.service
```
