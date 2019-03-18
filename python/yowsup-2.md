<!-- TITLE: Yowsup 2 -->

Centos7
# Install

```sh
sudo yum -y install epel-release
sudo yum -y install git
sudo yum -y install python34
sudo yum -y install python-dateutil
sudo yum -y install python34-devel
sudo yum -y install ncurses-devel
sudo yum -y install protobuf-python
sudo yum -y install python34-cryptography

git clone https://github.com/tgalal/python-axolotl-curve25519.git
cd python-axolotl-curve25519
sudo python3.4 setup.py install

git clone https://github.com/tgalal/yowsup.git
cd yowsup
sudo python3.4 setup.py install
```

Upgrading version

Backup the file env_android.py


```sh
cp /usr/lib/python3.4/site-packages/yowsup2-2.5.7-py3.4.egg/yowsup/env/env_android.py /tmp/env_android.py.backup
```


And apply these changes in the  /usr/lib/python3.4/site-packages/yowsup2-2.5.7-py3.4.egg/yowsup/env/env_android.py file


```diff
20c20
<     _MD5_CLASSES = "uts7K11+PDyZE5R0ou+2Sw=="
---
>     _MD5_CLASSES = "DAPy33TbNMg0Yuplp2II0A=="
23c23
<     _VERSION = "2.17.337"
---
>     _VERSION = "2.18.339"
```


# Testing


```sh
$ yowsup-cli registration --requestcode sms --phone 51999999999 --cc 51 --mcc 716 --mnc 06 --env android 

yowsup-cli  v2.0.15
yowsup      v2.5.7

Copyright (c) 2012-2016 Tarek Galal
http://www.openwhatsapp.org

This software is provided free of charge. Copying and redistribution is
encouraged.

If you appreciate this software and you would like to support future
development please consider donating:
http://openwhatsapp.org/yowsup/donate


INFO:yowsup.common.http.warequest:b'{"login":"51999999999","status":"sent","length":6,"method":"sms","retry_after":65,"sms_wait":65,"voice_wait":65}\n'
method: b'sms'
status: b'sent'
login: b'51999999999'
length: 6
retry_after: 65
```

Then an SMS will arrive with a register code example: 602025


```sh
$ yowsup-cli registration --register 602025 --phone 51999999999 --cc 51 --env android
yowsup-cli  v2.0.15
yowsup      v2.5.7

Copyright (c) 2012-2016 Tarek Galal
http://www.openwhatsapp.org

This software is provided free of charge. Copying and redistribution is
encouraged.

If you appreciate this software and you would like to support future
development please consider donating:
http://openwhatsapp.org/yowsup/donate


INFO:yowsup.common.http.warequest:b'{"status":"ok","login":"51999999999","type":"existing","edge_routing_info":"CAUIAg==","chat_dns_domain":"fb","pw":"3zr54a4M+jODiEsdfg2323=","expiration":4444444444.0,"kind":"free","price":"$0.99","cost":"0.99","currency":"USD","price_expiration":1547151113}\n'
kind: b'free'
cost: b'0.99'
pw: b'sdfg+4zr54aNM='
login: b'51999999999'
currency: b'USD'
expiration: 4444444444.0
price: b'$0.99'
type: b'existing'
status: b'ok'
price_expiration: 1544151913
```

Create a file auth.txt with this information


```text
cc=51  #replace with your country code
phone=51999999999  #replace with your phone number 
password=sdfg+4zr54aNM= #your account's real password.
```

Then send a message


```sh
$ yowsup-cli demos -c auth.txt -s 51997999999 "Hola mundo"
```

Interactive mode


```sh
$ yowsup-cli demos -c auth.txt -y
```



# Solution to send images issue:

Use this fork:

```sh
git clone https://github.com/AragurDEV/yowsup.git
sudo pip3.4  install xvfbwrapper
sudo yum install -y python-xvfbwrapper.noarch
sudo yum install -y perl-Image-ExifTool.noarch
sudo yum install -y python-wand.noarch
sudo pip3 install pycrypto
cd yowsup
sudo python3.4 setup.py install
```


