---
layout: page
title: MySql
permalink: /mysql/
---

## Connect/Disconnect

```bash
mysql -u <user> -h <host> -p<passwd>
```

## Loading Data From File

```mysql
LOAD DATA INFILE '/temp/mydata.txt' INTO TABLE table1
FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' ESCAPED BY '\\'
```

## Modify Tables

```
CREATE TABLE table (field1 type1, field2 type2, ..., PRIMARY KEY (field1, field2))

CREATE TABLE new_tbl_name LIKE tbl_name
  [SELECT ... FROM tbl_name ...]

ALTER TABLE table ADD new_name_field1 type1 AFTER another_field
```

## User Management

```mysql
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
```

```mysql
GRANT ALL PRIVILEGES ON [database name].[table name] TO 'user'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT, INSERT, DELETE ON [database name].[table name] TO 'user'@'localhost' IDENTIFIED BY 'password';
REVOKE ALL PRIVILEGES ON [database name].[table name] FROM 'user'@'host'; -- one permission only
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user'@'host'; -- all permissions
```

```mysql
SET PASSWORD FOR 'user'@'host' = PASSWORD('new_pass')
```

## Reset Root Password

```bash
$ /etc/init.d/mysql stop
$ mysqld_safe --skip-grant-tables &
$ mysql # on another terminal
mysql> UPDATE mysql.user SET password=PASSWORD('newpasswrd') WHERE user='root';
## Kill mysqld_safe from the terminal, using Control + \
$ /etc/init.d/mysql start
```
