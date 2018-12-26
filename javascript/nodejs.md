<!-- TITLE: Nodejs -->

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

## From the EPEL Repository 

Tested in Centos


```sh
sudo yum install epel-release
sudo yum install nodejs
node --version
```

## From NodeSource
As root execute:

```sh
curl -sL https://rpm.nodesource.com/setup_11.x | bash -
sudo yum install -y nodejs
```

