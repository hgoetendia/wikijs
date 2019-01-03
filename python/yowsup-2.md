<!-- TITLE: Yowsup 2 -->
<!-- SUBTITLE: A quick summary of Yowsup 2 -->

Centos7
# Install

sudo yum -y install git
sudo yum -y install python
sudo yum -y install python-dateutil
sudo yum -y install python-devel
sudo yum -y install ncurses-devel
sudo yum -y install protobuf-python
sudo yum -y install python2-crypto

git clone https://github.com/tgalal/python-axolotl-curve25519.git
cd python-axolotl-curve25519
sudo python setup.py install

sudo yum -y install epel-release
sudo yum install python34-pip


git clone https://github.com/tgalal/yowsup.git
cd yowsup

