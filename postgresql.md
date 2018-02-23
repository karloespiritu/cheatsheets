---
layout: page
title: Postgresql
permalink: /postgresql/
---

## Basic Commands

### Login to postgresql
```bash
psql -U postgres
psql -d mydb -U myuser -W
psql -h myhost -d mydb -U myuser -W
psql -U myuser -h myhost "dbname=mydb sslmode=require" # ssl connection
```

### Default Admin Login
```bash
sudo -u postgres psql -U postgres
sudo -u postgres psql
```

### List databases on postgresql server
```
psql -l [-U myuser] [-W]
```

### Turn off line pager pagination in psql:
```
\pset pager
```

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
```bash
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

## Handy Queries

```sql
-- List procedure/function
SELECT * FROM pg_proc WHERE proname='__procedurename__';

-- List view (including the definition)
SELECT * FROM pg_views WHERE viewname='__viewname__';

-- Show DB table space in use
SELECT pg_size_pretty(pg_total_relation_size('__table_name__'));:

-- Show DB space in use
SELECT pg_size_pretty(pg_database_size('__database_name__'));

-- Show current user's statement timeout
show statement_timeout;

-- Show table indexes
SELECT * FROM pg_indexes WHERE tablename='__table_name__' AND schemaname='__schema_name__';

-- Get all indexes from all tables of a schema:
SELECT
   t.relname AS table_name,
   i.relname AS index_name,
   a.attname AS column_name
FROM
   pg_class t,
   pg_class i,
   pg_index ix,
   pg_attribute a,
   pg_namespace n
WHERE
   t.oid = ix.indrelid
   AND i.oid = ix.indexrelid
   AND a.attrelid = t.oid
   AND a.attnum = ANY(ix.indkey)
   AND t.relnamespace = n.oid
   AND n.nspname = 'kartones'
ORDER BY
   t.relname,
   i.relname

-- Queries being executed at a certain DB
SELECT datname, application_name, pid, backend_start, query_start, state_change, state, query
  FROM pg_stat_activity
  WHERE datname='__database_name__';

-- Get all queries from all dbs waiting for data (might be hung)
SELECT * FROM pg_stat_activity WHERE waiting='t';
```

### Query analysis

```
-- See the query plan for the given query
EXPLAIN __query__

-- See and execute the query plan for the given query
EXPLAIN ANALYZE __query__

-- Collect statistics
ANALYZE [__table__]
```

## Source:
[PostgreSQL 9.6.0 Documentation](https://www.postgresql.org/docs/9.6/static/app-psql.html)
[PostgreSQL Exercises](https://pgexercises.com)
