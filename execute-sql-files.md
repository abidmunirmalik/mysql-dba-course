## EXECUTE .SQL FILES IN MYSQL SERVER

### SOURCE MySQL SHELL COMMAND
```sh
mysql>source employees.sql
mysql>\. employees.sql
```

### MYSQL CLIENT PROGRAM 
```sh
mysql --host=localhost employees < employees.sql
```

### SHELL SCRIPT
```sh
vi employees.sh
msyql --host=localhost employees < $1
chmod u+x employees.sh
bash employees.sh employees.sql
```

### PIPE METHOD 
```sh
cat employees.sql | mysql --host=localhost
```
