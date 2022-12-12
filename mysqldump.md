## MYSQLDUMP

### HELP
```sh
man mysqldump
```

### BACKUP TABLE
```sh
mysqldump world continents > continents.sql
mysqldump world continents --where="cid=5" > south_america.sql
mysqldump world --ignore-table=world.continents > no_continent_world.sql
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
