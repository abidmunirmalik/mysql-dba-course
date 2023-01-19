## INSTALL SPECIFIC VERSION OF PERCONA SERVER

### INSTALLATION STEPS
STEP 1. DOWNLOAD PERCONA MYSQL 8 REPOSITORY PACKAGE
```sh
wget https://repo.percona.com/yum/percona-release-latest.noarch.rpm
```

STEP 2. INSTALL PERCONA MYSQL REPO LOCALLY
```sh
sudo yum localinstall percona-release-latest.noarch.rpm
```

STEP 3. ENABLE REPO FOR PERCONA MySQL 8
```sh
sudo percona-release setup -y ps80
```

STEP 4. SET ENVIRONMENT VARIABLE
```sh
VERSION=8.0.26-16.1
BACKUP_VERSION=8.0.26-18.1
echo $VERSION
echo $BACKUP_VERSION
```

STEP 5. INSTALL MYSQL SERVER PACKAGES IN THIS ORDER
```sh
sudo yum -y install percona-server-shared-compat-$VERSION.el7.x86_64
sudo yum -y install percona-server-shared-$VERSION.el7.x86_64
sudo yum -y install percona-server-client-$VERSION.el7.x86_64
sudo yum -y install percona-server-server-$VERSION.el7.x86_64
sudo yum -y install percona-xtrabackup-80-$BACKUP_VERSION.el7.x86_64
```

STEP 6. VERIFY VERSION OF EACH PACKAGE
```sh
rpm -qa | grep -i percona-server
```

STEP 7. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
sudo systemctl enable mysqld.service
```

STEP 8. START MYSQL SERVICE
```sh
sudo systemctl start mysqld.service
```

STEP 9. CHECK STATUS OF MYSQL SERVICE
```sh
systemctl status mysqld
```

### VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
sudo lsof -u mysql
```
