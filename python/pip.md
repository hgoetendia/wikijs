<!-- TITLE: Pip -->

# Install


```sh
sudo yum install python34-pip.noarch
```

or

```sh
sudo yum install python36-pip.noarch

```

# Upgrade pip


```sh
pip install --upgrade pip
```

# Search with pip
Example, search python-dateutil package.

```sh
pip search python-dateutil
```

# List installed packages

```sh
$ pip list

DEPRECATION: Python 3.4 support has been deprecated. pip 19.1 will be the last one supporting it. Please upgrade your Python as Python 3.4 won't be maintained after March 2019 (cf PEP 429).
Package         Version
--------------- -------
pip             19.0.3 
python-dateutil 2.8.0  
setuptools      28.8.0 
six             1.12.0 

```

# Install requirements from file "requirements.txt"

Requirements file format:


```text
# To install specific version
package==version

# To install versión equal or grater
package>=version

# To install most recent versión
package
```

Examples:

`Pygame==1.7.1
Pygame>=1.7.1`


```sh
$cat requirements.txt 

consonance==0.1.2
python-axolotl==0.2.2
protobuf>=3.6.0
six==1.10
```



```sh
$ pip install -r requirements.txt
```


