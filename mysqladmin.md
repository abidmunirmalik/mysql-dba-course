## MYSQL ADMINISTRATION PROGRAM

### HELP
```sh
mysqladmin --help
```

### CREATE & DROP DATABASE 
```sh
mysqladmin --user=root --password create demo
mysql> \! mysqladmin --user=root --password drop demo
```

### COMMANDS WITH mysql_config_editor CONFIGURED
```sh
mysqladmin status
mysqladmin version
mysqladmin processlist
```
