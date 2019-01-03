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


```sh
psql -h myhost -d mydb -U myuser
```





