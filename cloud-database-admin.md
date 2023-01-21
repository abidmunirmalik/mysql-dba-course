## CLOUD DATABASE ADMINISTRATION

DigitalOcean $200 Credit for 60 Days: https://m.do.co/c/8722350423f7

### SETUP 2 VMs ON DIGITAL-OCEAN
```
1. Create New Project called `MySQL`
2. Create `Droplets`
3. Region: New York (please choose that is closer to you)
4. Choose Image: CentOS 7
5. Droplet Type: Basic
6. CPU Options: Regular(SSD) 1GB/1CPU
7. Authentication Method - SSH Key - New SSH Key `Key-Name: cloud-db`
8. Quantity: 2
9. Droplet-1 Name: primary & Droplet-2 Name: replica
10. Create
```

### DISABLE SELINUX & EDIT HOSTS FILE
```
1. Disable `selinux` on both primary & replica
2. Edit the `/etc/hosts` file to add friendly DNS name of target host
3. Reboot both Primary & Replica Server
```

### INSTALL MYSQL SERVER
https://github.com/abidmunirmalik/mysql-dba-course/blob/main/specific-version.md


### PERFORM SECURE INSTALLATION
```sh
grep password /var/log/mysqld.log
mysql_secure_installation
mysql --host=localhost --user=root --password
```

### CREATE DBA & REPLICATION ADMIN USERS - PRIMARY ONLY
```sql
CREATE USER IF NOT EXISTS bob IDENTIFIED WITH mysql_native_password BY 'P@ssw0rd123';
CREATE USER IF NOT EXISTS replication_admin IDENTIFIED WITH mysql_native_password BY 'P@ssw0rd123';
GRANT ALL PRIVILEGES ON *.* TO bob WITH GRANT OPTION;
GRANT REPLICATION SLAVE ON *.* TO replication_admin;
FLUSH PRIVILEGES;
```

### STORE AUTH CREDENTIALS
```sh
mysql_config_editor set --user=bob --password
```
