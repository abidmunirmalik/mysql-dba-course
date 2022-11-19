## DOWNLOAD AND LOCAL INSTALL FROM RPMs

### INSTALLATION STEPS
STEP 1. DOWNLOAD PERCONA MYSQL 8 REPOSITORY PACKAGE
```sh
wget https://repo.percona.com/yum/percona-release-latest.noarch.rpm
```

STEP 2. DOWNLOAD INDIVIDUAL RPM PACKAGES
```sh
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.28-20/binary/redhat/7/x86_64/percona-server-server-8.0.28-20.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.28-20/binary/redhat/7/x86_64/percona-server-client-8.0.28-20.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.28-20/binary/redhat/7/x86_64/percona-server-shared-8.0.28-20.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.28-20/binary/redhat/7/x86_64/percona-server-shared-compat-8.0.28-20.1.el7.x86_64.rpm
```

STEP 3. INSTALL REPO
```sh
sudo yum localinstall percona-release-latest.noarch.rpm
```

STEP 4. ENABLE REPO FOR PERCONA MySQL 8
```sh
sudo percona-release setup -y ps80
```

STEP 5. LOCAL INSTALL ALL PACKAGES
```sh
sudo yum localinstall percona-server-*.rpm
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
