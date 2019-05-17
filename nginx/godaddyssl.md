<!-- TITLE: Godaddy SSL Certs with NGINX -->

Find de key file that godday gaves you `example.com.key` then donwload the zip cert file in godaddy web.

Join the files
```sh
cat 93rfs8dhf834hts.crt gd_bundle-g2-g1.crt > example.com.crt
```

Key and crt files had been saved in `/etc/godadycerts/example.com/` directory.


Modify de configuration file in nginx  `/etc/nginx/conf.d/example.com.conf`


```text

server {
  listen 80 default_server;
  listen [::]:80 default_server;
  server_name example.com www.example.com;
  return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl;
    #ssl_certificate /path/to/server.cert;
    #ssl_certificate_key /path/to/server.key;
    ssl_certificate      /etc/godadycerts/example.com/example.com.crt;
    ssl_certificate_key  /etc/godadycerts/example.com/example.com.key;

    server_name www.example.com;
    return 301 https://example.com$request_uri;
}


server {
  listen 443 ssl default deferred;

  server_name example.com;

  error_page 404 /;

  ssl_certificate      /etc/godadycerts/example.com/example.com.crt;
  ssl_certificate_key  /etc/godadycerts/example.com/example.com.key;
    	# Improve HTTPS performance with session resumption
  	ssl_session_cache shared:SSL:10m;
  	ssl_session_timeout 5m;

	# Enable server-side protection against BEAST attacks
  	ssl_prefer_server_ciphers on;
	ssl_ciphers ECDH+AESGCM:ECDH+AES256:ECDH+AES128:DH+3DES:!ADH:!AECDH:!MD5;
  		
  	# Disable SSLv3
  	ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

    	# Diffie-Hellman parameter for DHE ciphersuites
        # $ sudo openssl dhparam -out /etc/ssl/certs/dhparam.pem 4096
    	#ssl_dhparam /etc/ssl/certs/dhparam.pem;

	# Enable HSTS (https://developer.mozilla.org/en-US/docs/Security/HTTP_Strict_Transport_Security)
	add_header Strict-Transport-Security "max-age=63072000; includeSubdomains";  

  	# Enable OCSP stapling (http://blog.mozilla.org/security/2013/07/29/ocsp-stapling-in-firefox)
  	ssl_stapling on;
  	ssl_stapling_verify on;
  	ssl_trusted_certificate /etc/godadycerts/example.com/example.com.crt;
  	resolver 8.8.8.8 8.8.4.4 valid=300s;
  	resolver_timeout 5s;


  location / {
	
    root /var/www/myweb;

    location /api {
        proxy_set_header X-Forwarded-Host $host;
        proxy_set_header X-Forwarded-Server $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass http://127.0.0.1:9810;
        proxy_read_timeout 900;
        client_max_body_size 20M;
    }

  }


}

```

Check the configuration


```sh
nginx -t
```




