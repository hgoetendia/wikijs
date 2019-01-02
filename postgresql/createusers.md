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
bash-4.2$ createdb ws_gateway
```

