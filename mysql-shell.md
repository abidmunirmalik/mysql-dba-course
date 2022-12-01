## MYSQLSHELL

### HELP
```sh
mysqlsh --help
```

### RUN PROGRAM
```sh
mysqlsh --sql | --js | --py
mysqlsh --sql --uri=[user[:pass]@]host[:port][/db]
```

### USAGE EXAMPLES
```sh
$ mysqlsh root@localhost/schema
$ mysqlsh mysqlx://root@some.server:3307/world_x
$ mysqlsh --uri root@localhost --py -f sample.py sample param
$ mysqlsh root@targethost:33070 -s world_x -f sample.js
```

### SQL MODE
```sh
mysqlsh --sql --uri=bob@dbprod01:3306/world
SQL > show databases;
```
