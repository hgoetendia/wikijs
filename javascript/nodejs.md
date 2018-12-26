<!-- TITLE: Nodejs -->
<!-- SUBTITLE: A quick summary of Nodejs -->

# Install 

## From sources


```sh
sudo yum install gcc gcc-c++ wget
wget http://nodejs.org/dist/latest-v10.x/node-v10.14.2.tar.gz
tar xvf node-v10.14.2.tar.gz
cd node-v10.14.2
./configure
make
sudo make install
```

## From the EPEL Repository (Centos)

sudo yum install epel-release
sudo yum install nodejs
node --version
