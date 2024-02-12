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
