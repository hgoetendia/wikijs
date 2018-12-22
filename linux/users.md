<!-- TITLE: Users -->
<!-- SUBTITLE: A quick summary of Users -->

# Create a user.

```sh
sudo adduser juan
sudo passwd juan
```

# Add the user to group.
In this case we will user the `wheel` group:


```sh
usermod -aG wheel juan
```


