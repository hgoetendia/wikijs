<!-- TITLE: Nginx and Letsencrypt -->
<!-- SUBTITLE: Configuring Nginx with letsencrypt -->

# Configuring


Creating config file

```sh
sudo vim /etc/nginx/conf.d/mysite.conf
```

Settings

```text
server {

    listen [::]:443 ssl http2;
    listen 443 ssl http2;
    listen [::]:80;
    listen 80;

    server_name wiki.example.com;

    root /usr/share/nginx/html;

    charset utf-8;
    client_max_body_size 50M;

    location /.well-known/acme-challenge/ {
        allow all;
    }

    # RSA
    ssl_certificate /etc/letsencrypt/www.example.com/fullchain.cer;
    ssl_certificate_key /etc/letsencrypt/www.example.com/www.example.com.key;
    # ECDSA
    ssl_certificate /etc/letsencrypt/www.example.com_ecc/fullchain.cer;
    ssl_certificate_key /etc/letsencrypt/www.example.com_ecc/www.example.com.key;
		
    #Enable OCSP stapling (http://blog.mozilla.org/security/2013/07/29/ocsp-stapling-in-firefox)
    ssl_stapling on;
    ssl_stapling_verify on;
    ssl_trusted_certificate /etc/letsencrypt/www.example.com/fullchain.cer;


    location / {
        proxy_set_header Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_next_upstream error timeout http_502 http_503 http_504;
    }

}
```


This part:

```text
    #Enable OCSP stapling (http://blog.mozilla.org/security/2013/07/29/ocsp-stapling-in-firefox)
    ssl_stapling on;
    ssl_stapling_verify on;
    ssl_trusted_certificate /etc/letsencrypt/www.example.com/fullchain.cer;
```

Is to prevent the Firefox error: `A required TLS feature is missing. Error code: MOZILLA_PKIX_ERROR_REQUIRED_TLS_FEATURE_MISSING`

