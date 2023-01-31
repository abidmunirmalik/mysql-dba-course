## INSTALL PERCONA TOOLKIT

### INSTALLATION STEPS
STEP 1. DOWNLOAD PERCONA MYSQL 8 REPOSITORY PACKAGE
```sh
wget https://repo.percona.com/yum/percona-release-latest.noarch.rpm
```

STEP 2. INSTALL PERCONA MYSQL REPO LOCALLY
```sh
sudo yum localinstall -y percona-release-latest.noarch.rpm
```

STEP 3. ENABLE REPO FOR PERCONA MySQL 8
```sh
sudo percona-release setup -y ps80
```

STEP 4. INSTALL PERCONA TOOLKIT
```sh
sudo yum -y install percona-toolkit
```

STEP 5. VERIFY
```sh
sudo rpm -ql percona-toolkit
ls /usr/bin/pt-*
```
