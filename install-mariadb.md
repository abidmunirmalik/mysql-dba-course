## INSTALL MariaDB 10 COMMUNITY EDITION

### INSTALLATION STEPS
STEP 1. DOWNLOAD Script to setup MariaDB repo
```sh
wget https://downloads.mariadb.com/MariaDB/mariadb_repo_setup
```

STEP 2. CHANGE PERMISSIONS ON SCRIPT
```sh
chmod +x mariadb_repo_setup
```

STEP 3. RUN THE SCRIPT
```sh
sudo ./mariadb_repo_setup
```

STEP 4. INSTALL MARIADB COMMUNITY SERVER
```sh
sudo yum install MariaDB-server
```

STEP 5. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
sudo systemctl enable mariadb.service
```

STEP 6. START MARIADB SERVICE
```sh
sudo systemctl start mariadb.service
```

STEP 7. CHECK STATUS OF MARIADB SERVICE
```sh
systemctl status mariadb.service
```

### VERIFICATION
```sh
pidof mariadb
netstat -ntlp | grep 3306
sudo lsof -u mysql
```
