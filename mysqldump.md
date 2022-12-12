## MYSQLDUMP

### HELP
```sh
man mysqldump
```

### BACKUP TABLE
```sh
mysqldump world continents > continents.sql
```

### BACKUP DATABASE
```sh
mysqldump world > world.sql
```

### BACKUP MULTIPLE DATABASES
```sh
mysqldump --databases world,scratch > world_scratch.sql
```

### BACKUP ALL DATABASES
```sh
mysqldump --all-databases > all_databases.sql
```
