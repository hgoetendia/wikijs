<!-- TITLE: Netcat -->

# Netcat TCP server (forever listen) without -k option

```sh
#!/bin/bash

port=6700

while true;
do
    nc -l -p $port
done
exit 0

```
