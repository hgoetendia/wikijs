<!-- TITLE: Makedeb -->
<!-- SUBTITLE: A quick summary of Makedeb -->

This tutorial shows the most basic way of packaging a simple already-compiled program.

Decide on the name of your package. Standard debian notation is all lowercase in the following format:
Code:

`<project>_<major version>.<minor version>-<package revision>`

For example, you could name your first package...
Code:
helloworld_1.0-1
Create a directory to make your package in. The name should be the same as the package name.
Code:

```sh
mkdir helloworld_1.0-1

```
Pretend that the packaging directory is actually the root of the file system. Put the files of your program where they would be installed to on a system.
Code:

```sh
mkdir helloworld_1.0-1/usr
mkdir helloworld_1.0-1/usr/local
mkdir helloworld_1.0-1/usr/local/bin
cp "~/Projects/Hello World/helloworld" helloworld_1.0-1/usr/local/bin
```

Now create a special metadata file with which the package manager will install your program...
Code:

```sh
mkdir helloworld_1.0-1/DEBIAN
gedit helloworld_1.0-1/DEBIAN/control
```

Put something like this in that file...
Code:

```sh
Package: helloworld
Version: 1.0-1
Section: base
Priority: optional
Architecture: i386
Depends: libsomethingorrather (>= 1.2.13), anotherDependency (>= 1.2.6)
Maintainer: Your Name <you@email.com>
Description: Hello World
 When you need some sunshine, just run this
 small program!
 
 (the space before each line in the description is important)
```

Now you just need to make the package:
Code:


```sh
dpkg-deb --build helloworld_1.0-1
```



And you're done! 
