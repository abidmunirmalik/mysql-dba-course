## INSTALL PERCONA MYSQL 8 COMMUNITY EDITION

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

STEP 4. INSTALL MYSQL SERVER
```sh
sudo yum install percona-server-server
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
