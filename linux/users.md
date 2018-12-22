<!-- TITLE: Users -->

# Create a user.

```sh
sudo adduser juan
sudo passwd juan
```

# Add the user to group.
In this case we will user the `wheel` group:


```sh
sudo usermod -aG wheel juan
```


All commands were tested in Centos.