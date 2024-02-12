# CRUD REST API with Node.js, Express, and PostgreSQL by Tania Rascia

<https://blog.logrocket.com/crud-rest-api-node-js-express-postgresql/>

## Notes

`psql` is the PostgreSQL interactive terminal.

## Create a Role in Postgres

```sql
postgres=# CREATE ROLE me WITH LOGIN PASSWORD 'password';

-- Give `me` ability to create a database
postgres=# ALTER ROLE me CREATEDB;

-- run `\du` to list all roles and users:
postgres=# \du
                                       List of roles
    Role name     |                         Attributes                         | Member of 
------------------+------------------------------------------------------------+-----------
 hyosungbidol-lee | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
 me               | Create DB                                                  | {}

--  connect `postgres` with `me`:
psql -d postgres -U me

-- prompt now shoes `postgres=>` meaning we're no longer logged in as a superuser
postgres=> 
```

## Create a Database in Postgres

```sql
postgres=> CREATE DATABASE api;

-- Use the `list` command to see the available databases:
 List of databases
        Name         |      Owner       | Encoding | Collate | Ctype | ICU Locale | Locale Provider |             Access privileges             
---------------------+------------------+----------+---------+-------+------------+-----------------+-------------------------------------------
 api                 | me               | UTF8     | C       | C     |            | libc            | 
 auction             | hyosungbidol-lee | UTF8     | C       | C     |            | libc            | 

-- Connect to the new `api` database with `me` using the `\c` connect command:
postgres=> \c api
You are now connected to database "api" as user "me".
api=>
```

## Create a Table in Postgres

```sql
api=>
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(30),
  email VARCHAR(30)
);

-- Add data
INSERT INTO users (name, email)
  VALUES ('Jerry', 'jerry@example.com'), ('George', 'george@example.com');

api=> INSERT INTO users (name, email)
  VALUES ('Jerry', 'jerry@example.com'), ('George', 'george@example.com');
INSERT 0 2
api=> SELECT * FROM users;
 id |  name  |       email        
----+--------+--------------------
  1 | Jerry  | jerry@example.com
  2 | George | george@example.com
(2 rows)
```

