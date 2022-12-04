## MYSQL CONFIGURATION

### GET HELP
```sql
mysqld --verbose --help
mysqld --verbose --help | less
```

### ADD OPTION IN MY.CNF FILE
```sh
sudo vi /etc/my.cnf 
server-id = 1
sudo systemctl stop mysqld.service
sudo systemctl start mysqld.service
```

### CHANGE OPTION FILE LOCATION
```sh
sudo mkdir /etc/mysql
sudo cp /etc/my.cnf /etc/mysql/my.cnf
sudo mv /etc/my.cnf /etc/my.cnf.old
sudo systemctl restart mysqld
```

### START MYSQLD WITH STRACE
```sh
sudo systemctl stop mysqld
sudo strace mysqld
sudo systemctl stop mysqld
```

### OPTION FILE INCLUSION
```sh
sudo systemctl stop mysqld
sudo vi /etc/mysql/my.cnf
!includedir /etc/percona
sudo cp /etc/mysql/my.cnf /etc/percona/
sudo systemctl start mysqld
```

### MOVE DATA DIRECTORY
```sh
sudo systemctl stop mysqld
sudo mkdir /var/lib/mysql/data
sudo mv /var/lib/mysql/* /var/lib/mysql/data/
sudo vim /etc/percona/my.cnf
datdir = /var/lib/myql/data/
sudo systemctl start mysqld
```
