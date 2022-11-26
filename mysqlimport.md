## IMPORT DATA FILE IN MYSQL SERVER

### STEPS
```sh
mysql>show variables like 'secure_file_priv';
```

### COPY FILE
```sh
sudo mv staff.txt /var/lib/mysql-files/staff.txt
sudo chown mysql:mysql /var/lib/mysql-files/staff.txt
```

### IMPORT
```sh
mysqlimport --columns=fname,lname,title,isActive --delete employees /var/lib/mysql-files/staff.txt
```
