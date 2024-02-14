## INSTALL MYSQL 8 COMMUNITY EDITION ON Red Hat 9

### CREATE RED HAT 9 EC2 (AWS)
```sh
Instance type: t2.small
AWS Region: N. Virginia (us-east-1)
AMI: Red Hat Enterprise Linux 9(HVM), SSD Volume Type
AMI ID: ami-0fe630eb857a6ec83
AMI NAME: RHEL-9.3.0_HVM-20240117-x86_64-49-Hourly2-GP3
```

### VERIFY OS VERSION
```sh
cat /etc/os-release
```

### SEARCH MYSQL RPM
```sh
dnf search mysql-server
dnf info mysql-server.x86_64
```

### INSTALL MYSQL SERVER
```sh
dnf install mysql-server.x86_64
```

### ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
systemctl enable mysqld.service
```

### START MYSQL SERVICE
```sh
systemctl start mysqld.service
```

### CHECK STATUS OF MYSQL SERVICE
```sh
systemctl status mysqld.service
```

### VERIFICATION
```sh
pidof mysqld
```

### SECURE INSTALLATION
```sh
mysql_secure_installation
```
