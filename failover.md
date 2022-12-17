## PRIMARY-REPLICA FAILOVER PROCEDURE

### SET PRIMARY TO READ-ONLY
```sql
SET GLOBAL read_only = TRUE;
SET GLOBAL event_scheduler = 'OFF';
FLUSH TABLES WITH READ LOCK;
SHOW MASTER STATUS;
```

### CONFIRM REPLICA IS IN SYNC WITH PRIMARY
```sql
SHOW REPLICA STATUS\G
```

### DISABLE & SHUTDOWN PRIMARY & REPLICA
```sh
systemctl disable mysqld.service
systemctl stop mysqld.service
```

### CONFIGURE OLD-PRIMARY TO BECOME REPLICA 
```sh
log-bin           = /var/log/mysql/binlogs/prod01-binlog
log-bin-index     = /var/log/mysql/binlogs/prod01-binlog.index
relay-log         = /var/log/mysql/relay/prod01-relay
relay-log-index   = /var/log/mysql/relay/prod01-relay.index
report-host       = proddb01
read-only
skip-replica-start
```

### CONFIGURE OLD-REPLICA TO BECOME PRIMARY 
```sh
mkdir -p /var/log/mysql/binlogs
```
edit the replication.cnf file 
```sh
log-bin           = /var/log/mysql/binlogs/prod02-binlog
log-bin-index     = /var/log/mysql/binlogs/prod02-binlog.index
relay-log         = /var/log/mysql/relay/prod02-relay
relay-log-index   = /var/log/mysql/relay/prod02-relay.index
report-host       = proddb02
```

### START MYSQL ON NEW-PRIMARY
```sh
systemctl enable mysqld.service
systemctl start mysqld.service
```

### RESET REPLICA ON NEW-PRIMARY
```sql
SHOW REPLICA STATUS\G
RESET MASTER;
RESET REPLICA ALL;
SHOW REPLICA STATUS;
```

### START MYSQL ON OLD-PRIMARY
```sh
systemctl enable mysqld.service
systemctl start mysqld.service
```

### CONFIGURE OLD-PRIMARY TO BECOME REPLICA
```sql
RESET REPLICA ALL;
CHANGE REPLICATION SOURCE TO SOURCE_HOST='', SOURCE_USER='replicator', SOURCE_PASSWORD='', SOURCE_AUTO_POSITION=1;
START REPLICA;
SHOW REPLICA STATUS;
```

### RESET MASTER ON OLD-PRIMARY
```sql
RESET MASTER;
```

### VERIFY BOTH NEW-PRIMARY & NEW_REPLICA
```sql
SHOW MASTER STATUS:
SHOW REPLICAS;
SHOW REPLICA STATUS
```
