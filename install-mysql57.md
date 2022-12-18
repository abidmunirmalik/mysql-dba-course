## INSTALL MYSQL SERVER 5.7

### PERCONA REPO
```sh
sudo yum -y install https://repo.percona.com/yum/percona-release-latest.noarch.rpm
```

### ENABLE 5.7 REPO
```sh
sudo percona-release setup ps57
```

### INSTALL MYSQL 5.7
```sh
sudo yum -y install Percona-Server-server-57
```

### VERIFY MYSQL 5.7 
```sh
rpm -qa | grep -i percona
```

### START MYSQL
```sh
sudo systemctl start mysqld.service
```

### GRAB ROOT PASSWORD AND RUN SECURE INSTALLATION
```sh
grep temp /var/log/mysqld.log
mysql_secure_installation
```
