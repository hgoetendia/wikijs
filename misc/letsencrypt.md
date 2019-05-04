<!-- TITLE: Letsencrypt -->

# Fast way

```sh
sudo certbot --nginx certonly  -d www.myweb.com
```

# Automated version
Install the acme.sh client and obtain a Let's Encrypt certificate we will use acme.sh client. acme.sh is a pure UNIX shell script for obtaining SSL certificates from Let's Encrypt with zero dependencies. That makes it very lightweight in comparison to some other Acme protocol clients that require a lot of dependencies to run successfully.

Downloading and installing Acme.sh.

```sh
#as simple user
sudo mkdir /etc/letsencrypt
git clone https://github.com/Neilpang/acme.sh.git
cd acme.sh
sudo ./acme.sh --install --home /etc/letsencrypt --accountemail your_email@example.com
cd ~
```

Check the version.

```sh
/etc/letsencrypt/acme.sh --version
# v2.7.9
```

Obtain RSA and ECDSA certificates for your domain/hostname.

With Nginx 

```sh
#As simple user
# RSA 2048
sudo /etc/letsencrypt/acme.sh --issue --home /etc/letsencrypt -d www.example.com --webroot /usr/share/nginx/html --reloadcmd "sudo systemctl reload nginx.service" --accountemail your_email@example.com --ocsp-must-staple --keylength 2048
# ECDSA/ECC P-256
sudo /etc/letsencrypt/acme.sh --issue --home /etc/letsencrypt -d www.example.com --webroot /usr/share/nginx/html --reloadcmd "sudo systemctl reload nginx.service" --accountemail your_email@example.com --ocsp-must-staple --keylength ec-256 
```

After running the above commands, your certificates and keys will be in the following directories:


* For RSA: /etc/letsencrypt/wiki.example.com
* For ECC/ECDSA: /etc/letsencrypt/wiki.example.com_ecc

Configure NGINX with letsencrypt  [here](../nginx/letsencrypt)  