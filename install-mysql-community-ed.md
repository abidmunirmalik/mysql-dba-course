## INSTALL MYSQL 8 COMMUNITY EDITION

### INSTALLATION STEPS - AMAZON LINUX 2 (AL2)
STEP 1. DOWNLOAD MYSQL 8 REPOSITORY PACKAGE
```sh
wget https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
```

STEP 2. INSTALL MYSQL REPO LOCALLY
```sh
sudo yum localinstall mysql80-community-release-el7-3.noarch.rpm
```

STEP 3. Import Public Key for MySQL 8
```sh
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
```

STEP 4. INSTALL MYSQL SERVER
```sh
sudo yum install mysql-community-server
```

STEP 5. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
sudo systemctl enable mysqld.service
```

STEP 6. START MYSQL SERVICE
```sh
sudo systemctl start mysqld.service
```

STEP 7. CHECK STATUS OF MYSQL SERVICE
```sh
systemctl status mysqld
```

STEP 8. VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
sudo lsof -u mysql
```


### INSTALLATION STEPS - AMAZON LINUX 2023 (AL2023)

STEP 1. CREATE KEY PAIR

1. Create AWS account at https://console.aws.amazon.com
2. Login to AWS Console and search for EC2
3. Click **Key Pairs** under **Network & Security** Section on the left
4. Click **Create Key Pair**
   a. Name: **mysql-dba-course**
   b. Key pair type: **ED25519**
   c. Private key file format: **.pem** (linux) or **.ppk**(windows)
 5. Click **Create key pair**
 6. Move they key pair and change permissions
```
mv ~/Downloads/mysql-dba-course.pem ~/.ssh/
ls -ltr ~/.ssh/
chmod 600 ~/.ssh/mysql-dba-course.pem
```

STEP 2. CREATE SECURITY GROUP
1. Login to AWS Console and search for VPC
2. Click **Security Groups** under **Security** Section on the left
3. Click **Create Security Group**
   a. Name: **mysql-dba-course-sg**
   b. VPC: **default**
   c. Descriptiont: **SG for mysql-dba-course**
 4. Click **Inbound Rules** and create two inbound-rules
    a. Type: **SSH**
    b. Source: **Anywhere**
    c. Decription: **SSH Access**
    d. Type: **MySQL/Aurora**
    e. Source: **Anywhere**
    f. Description: **MySQL Access**


STEP 3. CREATE EC2 INSTANCE
1. Login to AWS Console and search for EC2
2. Make sure you are in **N. Virginia Region**
3. Click **Launch Instance**
   a. Name: **db02**
   b. Amazon Machine Image: **ami-01816d07b1128cd2d**
   c. Instance Type: **t2.small**
   d. Key Pair: **mysql-dba-course**
   e. Network Settings: **Auto-Assign public IP** Enabled
   f. Firewall (Security Group): **mysql-dba-course-sg**
   g. Configure Storage: **8GB & gp3**
 4. Click **Launch Instance**


STEP 4. CONNECT TO EC2 INSTANCE
1. Login to AWS Console and search for EC2
2. Make sure you are in **N. Virginia Region**
3. Select your EC2 and copy the **Public IP Address**
4. Open your terminal and connect to EC2 as:
```
ssh -i ~/.ssh/mysql-dba-course.pem ec2-user@3.82.66.171
```


STEP 5. DOWNLOAD MYSQL 8 REPOSITORY PACKAGE
```sh
cat /etc/os-release
cd /tmp
wget https://repo.mysql.com/mysql80-community-release-el9-5.noarch.rpm
```

STEP 6. INSTALL MYSQL REPO LOCALLY
```sh
sudo yum localinstall mysql80-community-release-el9-5.noarch.rpm
```


STEP 7. INSTALL MYSQL SERVER
```sh
sudo yum search mysql-community-server
sudo yum info mysql-community-server.x86_64
sudo yum install mysql-community-server.x86_64
```

STEP 8. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT
```sh
sudo systemctl enable mysqld.service
```

STEP 9. START MYSQL SERVICE
```sh
sudo systemctl start mysqld.service
```

STEP 10. CHECK STATUS OF MYSQL SERVICE
```sh
systemctl status mysqld
```

STEP 11. VERIFICATION
```sh
pidof mysqld
netstat -ntlp | grep 3306
sudo lsof -u mysql
```
