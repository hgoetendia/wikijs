<!-- TITLE: Creating users / databases -->

# Creating user

```sh
sudo su postgres
bash-4.2$ 

bash-4.2$ createuser --interactive
Enter name of role to add: juan  
Shall the new role be a superuser? (y/n) y
bash-4.2$
```

Alternative from postgresql prompt:

```pgsql
postgres=# CREATE USER juan WITH PASSWORD 'secretpass';
```

Alternative from postgresql prompt:

```pgsql
postgres=# ALTER ROLE juan WITH PASSWORD 'oyIP8222';
```

Grant role to user postgresql prompt:

```pgsql
postgres=# GRANT myrole TO juan;
```

# Show all users


```text
postgres=# \du                                                                                                                                                                                                               
                                      Lista de roles                                                                                                                                                                                          
 Nombre de rol  |                         Atributos                          | Miembro de                                                                                                                                                     
----------------+------------------------------------------------------------+------------                                                                                                                                                    
 oneuser        |                                                            | {consulta}                                                                                                                                                     
 myuser         |                                                            | {consulta}                                                                                                                                                     
 ouruser        |                                                            | {consulta}

```

# Creating database
As postgres user


```sh
bash-4.2$ createdb mydb
```

# Setting password and privileges

```pgsql
bash-4.2$ psql
psql (11.1)
Type "help" for help.

postgres=# alter user juan with encrypted password 'mysecretpassword';
ALTER ROLE
postgres=# grant all privileges on database mydb to juan; 
GRANT
postgres=# 

```

# Log into PostgreSQL database

Without password

```sh
psql -h myhost -d mydb -U myuser
```

With password


```sh
psql -d mydb -U myuser -W
psql -h myhost -d mydb -U myuser -W
```


If you cant, change the config file `/var/lib/pgsql/11/data/pg_hba.conf` (PostgreSQL Ver 11)

Original:


```pgsql
#TYPE  DATABASE        USER            ADDRESS                 METHOD

#"local" is for Unix domain socket connections only
local   all             all                                     peer
#IPv4 local connections:
host    all             all             127.0.0.1/32            ident
#IPv6 local connections:
host    all             all             ::1/128                 ident
#Allow replication connections from localhost, by a user with the
#replication privilege.
local   replication     all                                     peer
host    replication     all             127.0.0.1/32            ident
host    replication     all             ::1/128                 ident
```



Replace "ident" with "md5", so they look like this:


```pgsql
#TYPE  DATABASE        USER            ADDRESS                 METHOD

#"local" is for Unix domain socket connections only
local   all             all                                     md5
#IPv4 local connections:
host    all             all             127.0.0.1/32            md5
#IPv6 local connections:
host    all             all             ::1/128                 md5
#Allow replication connections from localhost, by a user with the
#replication privilege.
local   replication     all                                     peer
host    replication     all             127.0.0.1/32            ident
host    replication     all             ::1/128                 ident
```


After that you need reload config settings without restarting [goto manual](/postgresql/install#reload-config-settings-without-restarting).


Upon installation Postgres is set up to use "ident" authentication, meaning that it associates Postgres roles with a matching Unix/Linux system account. If a Postgres role exists, it can be signed in by logging into the associated Linux system account.





