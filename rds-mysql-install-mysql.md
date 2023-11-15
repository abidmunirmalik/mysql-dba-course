## AWS RDS MYSQL DATABASE ADMINISTRATION

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
```

### DISABLE SELINUX & EDIT HOSTS FILE
```sh
1. Disable `selinux` on both primary & replica
2. Edit the `/etc/hosts` file to add friendly DNS name of target host
3. Reboot both Primary & Replica Server
```

### INSTALL SPECIFIC MYSQL COMMUNITY SERVER
```sh
cd /tmp
wget https://downloads.mysql.com/archives/get/p/23/file/mysql-8.0.33-1.el7.x86_64.rpm-bundle.tar
tar xvf mysql-8.0.33-1.el7.x86_64.rpm-bundle.tar

yum localinstall mysql-community-client-plugins-8.0.33-1.el7.x86_64.rpm
yum localinstall mysql-community-common-8.0.33-1.el7.x86_64.rpm
yum localinstall mysql-community-libs-8.0.33-1.el7.x86_64.rpm
yum localinstall mysql-community-icu-data-files-8.0.33-1.el7.x86_64.rpm
yum localinstall mysql-community-client-8.0.33-1.el7.x86_64.rpm
yum localinstall mysql-community-server-8.0.33-1.el7.x86_64.rpm
rpm -qa | grep mysql

systemctl enable mysqld.service && systemctl start mysqld.service
systemctl status mysqld.service
pidof mysqld
netstat -ntlp | grep 3306
```


### PERFORM SECURE INSTALLATION
```sh
grep "temporary password" /var/log/mysqld.log
mysql_secure_installation
mysql --host=localhost --user=root --password
```

### CREATE DBA & REPLICATION ADMIN USERS - PRIMARY ONLY
```sql
CREATE USER IF NOT EXISTS bob IDENTIFIED WITH mysql_native_password BY 'XXXXX';
CREATE USER IF NOT EXISTS replication_admin IDENTIFIED WITH mysql_native_password BY 'XXXXX';
GRANT ALL PRIVILEGES ON *.* TO bob WITH GRANT OPTION;
GRANT REPLICATION SLAVE ON *.* TO replication_admin;
FLUSH PRIVILEGES;
```

### STORE AUTH CREDENTIALS
```sh
mysql_config_editor set --user=bob --password
```

### COPY BACKUP FROM PRIMARY TO REPLICA
```sh
systemctl stop mysqld.service
rm -rf /var/lib/mysql/* (Replica)
scp -r /var/lib/mysql/* root@replica.db.local:/var/lib/mysql/ (Primary)
chown -R mysql:mysql /var/lib/mysql (Replica)
systemctl start mysqld.service (Replica)
mysql_config_editor set --user=bob --password (Replica)
mysql
```

### PREPARE FOR GTID-BASED REPLICATION
```sh
vi /etc/my.cnf (Replica)
server-id                  = 2
systemctl stop mysqld.service && systemctl start mysqld.service
mysql
show global variables like 'server_id';

mkdir -p /var/log/mysql/binlogs
chown -R mysql:mysql /var/log/mysql/binlogs

vi /etc/my.cnf (Primary)
log-bin                    = /var/log/mysql/binlogs/primary-binlog
log-bin-index              = /var/log/mysql/binlogs/primary-binlog.index
binlog-expire-logs-seconds = 432000
gtid-mode                  = ON
enforce-gtid-consistency   = ON

vi /etc/my.cnf (Replica)
log-bin                    = /var/log/mysql/binlogs/replica-binlog
log-bin-index              = /var/log/mysql/binlogs/replica-binlog.index
binlog-expire-logs-seconds = 432000
gtid-mode                  = ON
enforce-gtid-consistency   = ON
```

### SETUP GTID-BASED REPLICATION
```sql
CHANGE REPLICATION SOURCE TO SOURCE_HOST='primary.db.local', SOURCE_USER='replication_admin', SOURCE_PASSWORD='XXXXX', SOURCE_AUTO_POSITION=1;
START REPLICA;
```

### AWS REPLICA SETUP
* Create EC2 on AWS as:
```
Security Group: mysql-sg with inbound rules:  3306(TCP) & 22(SSH)
AMI-ID: ami-09d3b3274b6c5d4aa
Key-Pair: mysql-dba-course
Block Device: 8GB
Instance Type: t2.micro
CPU: 1
Public IP Address: Yes
Name: cloud-replica
```

### INSTALL NMAP & PV
```sh
yum -y install epel-release (Linux)
yum -y install nmap-ncat pv tmux
amazon-linux-extras install epel -y (Amazon Linux)
yum -y install nmap-ncat pv tmux
xtrabackup --version
ncat --version
pv --version
tmux -V
```

### ONLINE STREAM BACKUP DATA
```sh
cd /var/lib/mysql (destination)
ncat --recv-only --listen 3306  | pv | xbstream -x (destination)
xtrabackup --backup --slave-info --stream=xbstream | ncat destination_server 3306 (source)
xtrabackup --prepare --target-dir=/var/lib/mysql (destination)
vi /etc/my.cnf
server-id = 3
chown -R mysql:mysql /var/lib/mysql
systemctl start mysqld
mysql
mysql -h primary.db.local -u bob -p

mkdir -p /var/log/mysql/binlogs
chown -R mysql:mysql /var/log/mysql/binlogs

vi /etc/my.cnf
server-id                  = 30
log-bin                    = /var/log/mysql/binlogs/cloud-replica-binlog
log-bin-index              = /var/log/mysql/binlogs/cloud-replica-binlog.index
binlog-expire-logs-seconds = 432000
gtid-mode                  = ON
enforce-gtid-consistency   = ON
report-host                = cloud-replica.db.local

systemctl stop mysqld.service && systemctl start mysqld.service
mysql
SET GLOBAL gtid_purged='d10df700-993f-11ed-b8b1-5e2741d17760:1-11';
STOP REPLICA;
RESET REPLICA ALL;
CHANGE REPLICATION SOURCE TO SOURCE_HOST='primary.db.local', SOURCE_USER='replication_admin', SOURCE_PASSWORD='XXXXX', SOURCE_AUTO_POSITION=1;
START REPLICA;
SHOW REPLICA STATUS\G
```
**Note:** On EC2, add an entry in `/etc/hosts` for `primary.db.local` to reflect it's public ip address as:
```sh
123.345.567.789  primary.db.local
```
