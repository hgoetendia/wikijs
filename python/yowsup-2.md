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
>     _MD5_CLASSES = "YqW9KfOVL6cRD8aiNh8l6w=="
23c23
<     _VERSION = "2.17.337"
---
>     _VERSION = "2.18.45"
```


