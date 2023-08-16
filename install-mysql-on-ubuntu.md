## INSTALL MYSQL 8 COMMUNITY EDITION ON UBUNTU

STEP 1. VERIFY OS VERSION
```sh
lsb_release -a
```

STEP 2. RUN UPDATES 
```sh
sudo apt update
```

STEP 3. INSTALL MYSQL SERVER
```sh
sudo apt install mysql-community-server
```

STEP 4. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
sudo systemctl enable mysql.service
```

STEP 5. START MYSQL SERVICE
```sh
sudo systemctl start mysql.service
```

STEP 6. CHECK STATUS OF MYSQL SERVICE
```sh
systemctl status mysql.service
```

### VERIFICATION
```sh
pidof mysqld
sudo lsof -u mysql
```

### SECURE INSTALLATION
```sh
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'P@ssw0rd123';
exit
mysql -u root -p
ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
exit
sudo mysql_secure_installation
Y
2
Y
Y
Y
Y
```
