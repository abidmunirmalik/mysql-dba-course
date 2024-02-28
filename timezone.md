## MYSQL_TZINFO_TO_SQL TIME ZONE DATA

The mysql_tzinfo_to_sql utility is used in MySQL to load the time zone tables. These tables are required for proper functioning of time zone support in MySQL. The utility reads the time zone data files and generates SQL statements that can be used to populate the mysql database with the necessary time zone information.

### HELP
```sh
man mysql_tzinfo_to_sql
```

### LOAD TIME ZONE DATA
```sh
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root -p mysql
```

### check the timezone data in MySQL
To check the timezone data in MySQL, you can query the time_zone_name and time_zone tables in the mysql database. Here's an example:
USE mysql;

-- To see a list of available time zones
```sh
SELECT * FROM time_zone_name;
```
-- To see details about a specific time zone (replace 'America/New_York' with the desired timezone)
```sh
SELECT * FROM time_zone WHERE Name = 'America/New_York';
```
