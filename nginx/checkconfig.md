<!-- TITLE: Nginx Basic commands -->

# Install Nginx 

Centos/RedHat
```sh
sudo yum install -y nginx
```

# Enable and start Nginx. 

Centos/RedHat

```sh
sudo systemctl enable nginx.service
sudo systemctl start nginx.service
```

# Check the configuration.

```sh
sudo nginx -t
```

# Reload Nginx.
Centos/RedHat

```sh
sudo systemctl reload nginx.service
```

