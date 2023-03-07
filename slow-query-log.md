## MySQL Slow Query Log

### Check if Slow Query Log is Enabled
```
 show global variables like '%slow%';
 ```

### Slow Query Log Setup
```
mkdir -p /var/log/mysql/slow-logs
touch /var/log/mysql/slow-logs/slow-logs.log
chown -R mysql:mysql /var/log/mysql/
```

### Enable Slow Query Log
```
vim /etc/my.cnf

[mysqld]
slow-query-log
log-queries-not-using-indexes
log-slow-admin-statements
log-slow-extra
log-slow-replica-statements (Only Replica)
slow-query-log-file = /var/log/mysql/slow-logs/slow-logs.log
long-query-time = 1
```

### Restart MySQL Service
```
systemctl stop mysqld.service && sudo systemctl start mysqld.service
```

### Verify if Slow Query Log has been configured
```
mysql> show global variables like '%slow%';
```
