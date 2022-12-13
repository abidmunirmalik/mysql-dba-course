## XTRABACKUP HOT BACKUP TOOL

### INSTALLATION STEPS

STEP 1. ENABLE REPO FOR PERCONA MySQL 8
```sh
sudo percona-release setup -y ps80
```

STEP 2. SET ENVIRONMENT VARIABLE
```sh
VERSION=8.0.28-20.1
echo $VERSION
```

STEP 3. INSTALL XTRABACKUP
```sh
sudo yum install percona-xtrabackup-80-8.0.28-20.1.el7
```

STEP 4. VERIFY
```sh
rpm -qa | grep -i percona-server
```


### TAKE HOT BACKUP
```sh
mysql_config_editor set --user=bob --login-path=client --password
xtrabackup --backup --target-dir=/var/log/mysql/hotbackup
xtrabackup --prepare --target-dir=/var/log/mysql/hotbackup
```

### RESTORE FROM HOT BACKUP
```sh
sudo -i
cd /var/log/hotbackup
systemctl stop mysqld.service
rm -rf /var/lib/mysql/prod
rm -rf /var/lib/mysql/innodb
mkdir /var/lib/mysql/prod
mkdir /var/lib/mysql/innodb
cp -r mysql performance_schema scratch sys world *.ibd /var/lib/mysql/prod/
cp ib_buffer_pool  ibdata1  ibdata2  ibtmp1  undo_001  undo_002 /var/lib/mysql/innodb/
rm -f /var/log/mysql/redologs/ib_logfile*
cp ib_logfile0  ib_logfile1 /var/log/mysql/redologs/
rm -f /var/log/mysql/binlogs/prod-binlog.*
rm -f /var/log/mysql/doublewrite/#ib_16384_*
chown -R mysql:mysql /var/log/mysql/
chown -R mysql:mysql /var/lib/mysql/
systemctl start mysqld
```
