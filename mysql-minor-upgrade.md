## MYSQL MINOR VERSION UPGRADE

### CHECK INSTALLED VERSION
```sh
rpm -qa | grep -i percona
yum install -y https://repo.percona.com/yum/percona-release-1.0-27.noarch.rpm
percona-release setup -y ps80
```

### DOWNLOAD NEWER MINOR VERSION - 8.0.30
```sh
ls -ltr *.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-shared-compat-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-shared-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-client-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-Server-LATEST/Percona-Server-8.0.30-22/binary/redhat/7/x86_64/percona-server-server-8.0.30-22.1.el7.x86_64.rpm
wget https://downloads.percona.com/downloads/Percona-XtraBackup-LATEST/Percona-XtraBackup-8.0.30-23/binary/redhat/7/x86_64/percona-xtrabackup-80-8.0.30-23.1.el7.x86_64.rpm
```

### DOWNLOAD NEWER MINOR VERSION - 8.0.33
```sh
cd /tmp
yum install percona-server-server-8.0.33-25.1.el7.x86_64 --downloadonly --downloaddir=/tmp
yum install percona-server-client-8.0.33-25.1.el7.x86_64 --downloadonly --downloaddir=/tmp
yum install percona-server-shared-8.0.33-25.1.el7.x86_64 --downloadonly --downloaddir=/tmp
yum install percona-server-shared-compat-8.0.33-25.1.el7.x86_64 --downloadonly --downloaddir=/tmp
wget https://downloads.percona.com/downloads/Percona-XtraBackup-8.0/Percona-XtraBackup-8.0.33-27/binary/redhat/7/x86_64/percona-xtrabackup-80-8.0.33-27.1.el7.x86_64.rpm
```

### ENABLE MYSQL 8 REPO
```sh
sudo percona-release setup -y ps80
```

### SET MINOR VERSION VARIABLE - 8.30
```sh
VERSION=8.0.30-22.1
echo $VERSION
```

### SET MINOR VERSION VARIABLE - 8.33
```sh
VERSION=8.0.33-25.1
echo $VERSION
```

### SHUTDOWN MYSQL SERVER SERVICE
```sh
sudo systemctl stop mysqld
```

### INSTALL NEW MINOR VERSION - 8.0.30
```sh
sudo yum localinstall percona-server-shared-compat-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-shared-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-client-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-server-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-xtrabackup-80-8.0.30-23.1.el7.x86_64.rpm
```

### INSTALL NEW MINOR VERSION - 8.0.33
```sh
sudo yum localinstall percona-server-shared-compat-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-shared-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-client-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-server-server-$VERSION.el7.x86_64.rpm
sudo yum localinstall percona-xtrabackup-80-8.0.33-27.1.el7.x86_64.rpm
```

### VERIFY NEW RPM VERSION
```sh
rpm -qa | grep -i percona-server
```

### START MYSQL SERVICE
```sh
sudo systemctl start mysqld.service
```

### VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
mysql --version
```
