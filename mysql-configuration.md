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
