## INSTALL MYSQL 8 COMMUNITY EDITION

### INSTALLATION STEPS
STEP 1. DOWNLOAD MYSQL 8 REPOSITORY PACKAGE
```sh
$ sudo rpm -Uvh https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
```

STEP 2. DISABLE ALL OTHER MYSQL REPOS
```sh
$ sudo sed -i 's/enabled=1/enabled=0/' /etc/yum.repos.d/mysql-community.repo
```

STEP 3. ENABLE MYSQL 8 REPO AND INSTALL MYSQL SERVER
```sh
$ sudo yum -y --enablerepo=mysql80-community install mysql-community-server
```

STEP 4. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
$ sudo systemctl enable mysqld
```

STEP 5. START MYSQL SERVICE
```sh
$ sudo systemctl start mysqld.service
```

STEP 6. CHECK STATUS OF MYSQL SERVICE
```sh
$ systemctl status mysqld
```

### EXTRA TOOLS
```sh
$ sudo yum install net-tools
$ sudo yum install lsof
```
