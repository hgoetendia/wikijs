<!-- TITLE: SSH -->

# SSH across 3 machines
* Source localhost port 8002
* Target 192.168.5.10 port 5432
* Across 192.168.214.10, in this server must exist the OS user `myuserexample`

```sh
ssh -vvv -N -L localhost:8002:192.168.5.10:5432 myuserexample@192.168.214.10
```


# SSH login without password
* Source host: source
* Target host: target
* Example target username: horacio


```sh
ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/horacio/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/horacio/.ssh/id_rsa.
Your public key has been saved in /home/horacio/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:XXXXXXXXXXXXXXXX horacio@XXX
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|.    .           |
|+o+ +            |
|+@+= + .         |
|Xo + S           |
|*=o = .          |
|@*+ o o          |
|*oo=             |
|.o=..            |
+----[SHA256]-----+
```

Next execute ssh-copy-id (you will need horacio's password)

```sh
ssh-copy-id horacio@target
```

Alternatively if you dont have `ssh-copy-id` you can execute this from source:

```sh
cat ~/.ssh/id_rsa.pub | ssh horacio@target "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```





