<!-- TITLE: Virtual enviroments and packages -->

Sometimes it is not possible for one Python installation to meet the requirements of every application. If application A needs version 1.0 of a particular module but application B needs version 2.0, then the requirements are in conflict and installing either version 1.0 or 2.0 will leave one application unable to run.

The solution for this problem is to create a virtual environment, a self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages.

# Install


```sh
sudo pip install virtualenv
```


# Create a virtual enviroment

```sh
python3 -m venv my-env
```
# Activate a virtual envioroment


```sh
source my-env/bin/activate
```
# Managing Packages with pip