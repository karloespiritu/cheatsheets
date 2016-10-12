---
layout: page
title: Postgresql
permalink: /postgresql/
---

## Basic Commands

### Login to postgresql

```bash
psql -d mydb -U myuser -W
psql -h myhost -d mydb -U myuser -W
psql -U myuser -h myhost "dbname=mydb sslmode=require" # ssl connection
```

### Default Admin Login
sudo -u postgres psql -U postgres
sudo -u postgres psql

### List databases on postgresql server

```
psql -l [-U myuser] [-W]
```

### Turn off line pager pagination in psql:
\pset pager


### Determine system tables

```
select * from pg_tables where tableowner = 'postgres';
```

### List databases from within a pg shell

```
\l
```

### List databases from UNIX command prompt

```
psql -U postgres -l
```

### Describe a table

```
\d tablename
```
### Quit psql

```
\q
```

### Switch postgres database within admin login shell

```
\connect databasename
```

### Reset a user password as admin
```
alter user usertochange with password 'new_passwd';
```

### Show all tables
```
\dt
```

### List all Schemas
```
\dn
```

### List all users
```
\du
```

### Load data into postgresql

```bash
psql -W -U username -H hostname < file.sql
```

### Dump (Backup) Data into file

```
pg_dump -W -U username -h hostname database_name > file.sql
```

### Increment a sequence
```sql
SELECT nextval('my_id_seq');
```

### Create new user
```sql
CREATE USER lemmy WITH PASSWORD 'myPassword';
# or

sudo -u postgres createuser lemmy -W
```

### Change user password
```sql
ALTER USER Postgres WITH PASSWORD 'mypass';
```

### Grant user createdb privilege
```sql
ALTER USER myuser WITH createdb;
```

### Create a superuser user
```bash
create user mysuper with password '1234' SUPERUSER
# or even better
create user mysuper with password '1234' SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN REPLICATION;
# or
sudo -u postgres createuser lemmy -W -s
```

### Upgrade an existing user to superuser
```
alter user mysuper with superuser;
# or even better
alter user mysuper with SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN REPLICATION
```

### Show Database Version
```
SELECT version();
```

### Change Database Owner
```sql
alter database database_name owner to new_owner;
```

### Copy a database
```sql
CREATE DATABASE newdb WITH TEMPLATE originaldb;
```

### View Database Connections
```sql
SELECT * FROM pg_stat_activity;
```

### View show data directory (works on 9.1+)
```sql
show data_directory;
```

### Show run-time parameters
```sql
show all;
select * from pg_settings;
```

### Show the block size setting
```bash
# show block_size;
 block_size
------------
 8192
(1 row)
```

### Show stored procedure source
```sql
SELECT prosrc FROM pg_proc WHERE proname = 'procname'
```

### Grant examples
```
# readonly to all tables for myuser
grant select on all tables in schema public to myuser;
# all privileges on table1 and table2 to myuser
grant all privileges on table1, table2, table3 to myuser;
```

### Restore Postgres .dump file
```
pg_restore --verbose --clean --no-acl --no-owner -h localhost -U myuser -d mydb latest.dump
```
[source](https://gist.github.com/kagemusha/1569836)

### Find all active sessions and kill them (i.e. for when needing to drop or rename db)
Source: [http://stackoverflow.com/questions/5408156/how-to-drop-a-postgresql-database-if-there-are-active-connections-to-it](http://stackoverflow.com/questions/5408156/how-to-drop-a-postgresql-database-if-there-are-active-connections-to-it)

```sql
# Postgres 9.2 and above
SELECT pg_terminate_backend(pg_stat_activity.pid)
FROM pg_stat_activity
WHERE pg_stat_activity.datname = 'TARGET_DB'
 AND pid <> pg_backend_pid();

# Postgres 9.1 and below
SELECT pg_terminate_backend(pg_stat_activity.procpid)
FROM pg_stat_activity
WHERE pg_stat_activity.datname = 'TARGET_DB'
AND procpid <> pg_backend_pid();
```

## Source:
[PostgreSQL 9.6.0 Documentation](https://www.postgresql.org/docs/9.6/static/app-psql.html)
