<!-- TITLE: PostgreSQL/Install -->

Centos 7 tested with PostgreSQL 11
# Configure yum repo

```sh
sudo rpm -Uvh https://yum.postgresql.org/11/redhat/rhel-7-x86_64/pgdg-centos11-11-2.noarch.rpm
sudo yum -y install postgresql11-server
```

# Initializing PGDATA

We need create data directory and other configuration files.


```sh
sudo /usr/pgsql-11/bin/postgresql-11-setup initdb
```
# Enabling and starting service

```sh
sudo systemctl enable postgresql-11.service
sudo systemctl start postgresql-11.service
```
# Checking
As root

```sh
su - postgres -c "psql"
psql (11.1)
Type "help" for help.

postgres=#
```

# Setting password for `postgres` user

As postgres user

```pgsql
postgres=# \password postgres
```

# Reload config settings without restarting 

* Usrion `systemctl`


```sh
$ sudo systemctl reload postgresql
```

* Using `pg_ctl`

As postgres user

```sh
/usr/pgsql-11/bin/pg_ctl reload
```

* Using SQL


```sql
SELECT pg_reload_conf();
```


