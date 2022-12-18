### MYSQL MAJOR VERSION UPGRADE

### DOWNLOAD MYSQL SHELL 
```sh
wget https://dev.mysql.com/get/Downloads/MySQL-Shell/mysql-shell-8.0.31-1.el7.x86_64.rpm
```

### RUN CHECK FOR VERSION UPGRADE
```sh
 mysqlsh -- util check-for-server-upgrade root@localhost --target-version=8.0.30 --output-format=JSON --config-path=/etc/my.cnf
 ```
 
### CHECK INSTALLED VERSION
```sh
rpm -qa | grep -i percona
```

### DOWNLOAD NEWER MINOR VERSION
```sh
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-shared-compat-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-shared-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-client-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-server-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-XtraBackup-LATEST/Percona-XtraBackup-8.0.30-23/binary/redhat/7/x86_64/percona-xtrabackup-80-8.0.30-23.1.el7.x86_64.rpm
```

### ENABLE MYSQL 8 REPO
```sh
sudo percona-release setup -y ps80
```

### SET MINOR VERSION VARIABLE
```sh
VERSION=8.0.30-22.1
echo $VERSION
```

### SHUTDOWN MYSQL SERVER SERVICE
```sh
sudo systemctl stop mysqld
```

### INSTALL NEW MINOR VERSION
```sh
sudo yum localinstall percona-server-shared-compat-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-shared-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-client-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-server-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-xtrabackup-80-8.0.30-23.1.el7.x86_64.rpm
```

### VERIFY NEW RPM VERSION
```sh
rpm -qa | grep -i percona-server
```

### START MYSQL SERVICE
```sh
sudo systemctl start mysqld.service
```

### VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
mysql --version
```
