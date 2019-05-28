<!-- TITLE: Libzdb -->

# Install from sources

[Libzdb](http://www.tildeslash.com/libzdb/#)


`configure: WARNING: mysql_config is required to build libzdb with mysql
`

Dependencies:

```sh
sudo apt-get install libmysqlclient-dev
./configure
```
Last lines of summary
```text
..
checking for an ANSI C-conforming const... yes
checking whether byte ordering is bigendian... no
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating test/Makefile
config.status: creating zdb.pc
config.status: creating src/xconfig.h
config.status: executing libtool_patch commands
config.status: executing depfiles commands
config.status: executing libtool commands
+------------------------------------------------------------+
| License:                                                   |
| This is Open Source Software and use is subject to the GNU |
| GENERAL PUBLIC LICENSE, available in this distribution in  |
| the file COPYING.                                          |
|                                                            |
| By continuing this installation process, you are bound by  |
| the terms of this license agreement. If you do not agree   |
| with the terms of this license, you must abort the         |
| installation process at this point.                        |
+------------------------------------------------------------+
| Libzdb is configured as follows:                           |
|                                                            |
|   Optimized:                                    DISABLED   |
|   Protected:                                    DISABLED   |
|   Profiling:                                    DISABLED   |
|   Zild:                                         DISABLED   |
|   Sqlite3 unlock notification API:              DISABLED   |
|   Openssl:                                      DISABLED   |
|   Unit Tests Build:                             ENABLED    |
|------------------------------------------------------------|
|   SQLite3:                                      DISABLED   |
|   MySQL:                                        ENABLED    |
|   PostgreSQL:                                   DISABLED   |
|   Oracle:                                       DISABLED   |
+------------------------------------------------------------+

```

Compiling/installing


```sh
make
sudo make install
```

Fixing some personal issues

Edit 

```sh
sudo vim /usr/local/include/zdb/SQLException.h
```

Change:  

`#include <Exception.h>` to `#include "Exception.h"`

or add this flag in compilation

`-I/usr/include/zdb/`



# Install from package (Ubuntu)
Packages

libzbd-dev
libzdb11