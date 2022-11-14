## INSTALL MYSQL 8 COMMUNITY EDITION

### INSTALLATION STEPS
STEP 1. DOWNLOAD MYSQL 8 REPOSITORY PACKAGE
```sh
wget https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
```

STEP 2. INSTALL MYSQL REPO LOCALLY
```sh
sudo yum localinstall mysql80-community-release-el7-3.noarch.rpm
```

STEP 3. Import Public Key for MySQL 8
```sh
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
```

STEP 4. INSTALL MYSQL SERVER
```sh
sudo yum install mysql-community-server
```

STEP 5. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
sudo systemctl enable mysqld.service
```

STEP 6. START MYSQL SERVICE
```sh
sudo systemctl start mysqld.service
```

STEP 7. CHECK STATUS OF MYSQL SERVICE
```sh
systemctl status mysqld
```

### VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
sudo lsof -u mysql
```
