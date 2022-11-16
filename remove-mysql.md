## UNINSTALL MYSQL

### UNINSTALLATION STEPS
STEP 1. SEARCH FOR REPOSITORY PACKAGES
```sh
rpm -qa | grep -i release
```

STEP 2. REMOVE REPO
```sh
sudo yum -y remove percona-release
```

STEP 3. SEARCH FOR INSTALLED MYSQL PACKAGES
```sh
rpm -qa | grep -i percona
```

STEP 4. REMOVE MYSQL PACKAGES
```sh
sudo yum -y remove percona-server-shared
sudo yum -y remove percona-server-shared-compat
```

STEP 5. REMOVE MYSQL USER
```sh
grep mysql /etc/passwd
sudo userdel
sudo userdel -r mysql
```

STEP 6. REMOVE OTHER LEFTOVER FILES
```sh
ls /var/lib
ls /var/log
```

### VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
sudo lsof -u mysql
```
