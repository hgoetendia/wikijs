<!-- TITLE: Letsencrypt -->
<!-- SUBTITLE: A quick summary of Letsencrypt -->

# Basic
Install the Acme.sh client and obtain a Let's Encrypt certificate we will use Acme.sh client. Acme.sh is a pure UNIX shell script for obtaining SSL certificates from Let's Encrypt with zero dependencies. 
That makes it very lightweight in comparison to some other Acme protocol clients that require a lot of dependencies to run successfully.

Download and install Acme.sh.

```sh
#as simple user
sudo mkdir /etc/letsencrypt
git clone https://github.com/Neilpang/acme.sh.git
cd acme.sh
sudo ./acme.sh --install --home /etc/letsencrypt --accountemail your_email@example.com
cd ~
```
