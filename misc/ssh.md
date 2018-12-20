<!-- TITLE: SSH -->

# SSH across 3 machines
* Source localhost port 8002
* Target 192.168.5.10 port 5432
* Across 192.168.214.10, in this server must exist the OS user `myuserexample`

```sh
ssh -vvv -N -L localhost:8002:192.168.5.10:5432 myuserexample@192.168.214.10
```


