<!-- TITLE: Yowsup 2 -->
<!-- SUBTITLE: A quick summary of Yowsup 2 -->

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

