## DOWNLOAD SAMPLE WORLD DATABASE

### DOWNLOAD SAMPLE DATABASE ZIP FILE
```sh
wget https://downloads.mysql.com/docs/world-db.zip
```

### UNZIP .ZIP FILE
```sh
unzip world-db.zip
```

### EXECUTE world.sql SQL FILE
```sh
cd world-db
mysql < world.sql
```

### VERIFY
```sh
mysql> use world;
mysql>show tables;
mysql>SELECT * FROM country LIMIT 5;
```


