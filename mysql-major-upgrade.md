### MYSQL MAJOR VERSION UPGRADE

### DOWNLOAD MYSQL SHELL 
```sh
wget https://dev.mysql.com/get/Downloads/MySQL-Shell/mysql-shell-8.0.31-1.el7.x86_64.rpm
```

### RUN CHECK FOR VERSION UPGRADE
```sh
 mysqlsh -- util check-for-server-upgrade root@localhost --target-version=8.0.30 --output-format=JSON --config-path=/etc/my.cnf
 ```
 
