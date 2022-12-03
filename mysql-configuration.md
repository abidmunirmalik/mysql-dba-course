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
