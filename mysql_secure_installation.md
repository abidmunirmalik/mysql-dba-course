## MYSQL SECURE INSTALLATION

### STEPS
STEP 1. ACCESS ROOT PASSWORD
```sh
sudo grep password /var/log/mysqld.log
```

STEP 2. SEARCH FOR MYSQL_SECURE_INSTALLATION SCRIPT
```sh
which mysql_secure_installation
file /usr/bin/mysql_secure_installation
ls -ltr /usr/bin/mysql_secure_installation
```

STEP 3. RUN MYSQL_SECURE_INSTALLATION SCRIPT
```sh
sudo mysql_secure_installation
Enter password for user root:
The existing password for the user account root has expired. Please set a new password
New password:xxxxxx
Re-enter new password:xxxxxx
Change the password for root ? ((Press y|Y for Yes, any other key for No) : N
Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y
Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y
Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y
Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y
Success.

All done!
```

STEP 4. LOGIN TO MYSQL AND VERIFY
```sh
mysql --host=localhost --user=root --password
```

STEP 5. CHECK MYSQL VERSION
```sh
mysql> SELECT @@hostname, @@server_id, @@version;
```
