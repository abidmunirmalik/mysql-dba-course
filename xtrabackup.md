## INSTALL XTRABACKUP HOT BACKUP TOOL

### INSTALLATION STEPS

STEP 1. ENABLE REPO FOR PERCONA MySQL 8
```sh
sudo percona-release setup -y ps80
```

STEP 2. SET ENVIRONMENT VARIABLE
```sh
VERSION=8.0.28-20.1
echo $VERSION
```

STEP 3. INSTALL XTRABACKUP
```sh
sudo yum install percona-xtrabackup-80-8.0.28-20.1.el7
```

STEP 4. VERIFY
```sh
rpm -qa | grep -i percona-server
```
