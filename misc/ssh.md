<!-- TITLE: SSH -->

# SSH Keep alive connection

Add a file `~/.ssh/config` with these lines:


```text
ServerAliveInterval 60
ServerAliveCountMax 5
```


* ServerAliveInterval

Sets a timeout interval in seconds after which if no data has been received from the server, ssh will send a message through the encrypted channel to request a response from the server. The default is 0, indicating that these messages will not be sent to the server. This option applies to protocol version 2 only.

* ServerAliveCountMax

The default value is 3. If, for example, ServerAliveInterval is set to 15 and ServerAliveCountMax is left at the default, if the server becomes unresponsive, ssh will disconnect after approximately 45 seconds. This option applies to protocol version 2 only.

If ssh returns `Bad owner or permissions on ~/.ssh/config` 


```sh
chmod 600 ~/.ssh/config
```


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


From source:

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

Next execute ssh-copy-id (you will need horacio's password).

From source:

```sh
ssh-copy-id horacio@target
```

Alternatively if you dont have `ssh-copy-id` you can execute this from source:

```sh
cat ~/.ssh/id_rsa.pub | ssh horacio@target "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

Or


```text
[user@MBA:~]$ ssh-copy-id -p 222 otheruser@192.168.1.10
/usr/bin/ssh-copy-id: ERROR: No identities found
```

Solution

```text
[user@MBA:~]$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/horacio/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/user/.ssh/id_rsa.
Your public key has been saved in /Users/user/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:q4NEKaxIwKSlZTJxTW4BSJMBS1g8 user@MBA.local
The key's randomart image is:
+---[RSA 2048]----+

+----[SHA256]-----+
[user@MBA:~]$ ssh-copy-id -p 222 otheruser@192.168.1.10
```


# SSH SOCKS proxy

Local port: 12345
myuser: targetIP user
targetIP ssh listen port: 222 (default 22)


```sh
ssh -D 12345 myuser@targetIP -p222
```

If you are going to use a navigator with the proxy SOCKS will need these changes:

![Captura De Pantalla De 2019 01 14 13 46 38](/uploads/ssh/captura-de-pantalla-de-2019-01-14-13-46-38.png "Captura De Pantalla De 2019 01 14 13 46 38")



# SCP with Proxy 
Proxy: 192.168.1.2
Port: 222

Target server:192.168.10.5


```sh
scp -v -oProxyJump=myproxyuser@192.168.1.2:222 userintargetserver@192.168.10.5:/tmp/mydesiredfile.txt  ./
```

# SSH to machine A via B in one command

Note the -t on the first ssh command. Without it, it will fail:

Without "-t" Pseudo-terminal will not be allocated because stdin is not a terminal.
ssh_askpass: exec(/usr/bin/ssh-askpass): No such file or directory
Permission denied, please try again.
[...]
It will force a real TTY to be allocated


```sh
ssh -t myuser1@192.168.1.1 -v ssh otheruser@10.10.10.2
```




# SSH Errors
## bind: Cannot assign requested address                                                                                                                                                                                                         

```sh
$ ssh -D 12345  myuser@192.168.1.6 -p222
bind: Cannot assign requested address
Last login: Fri Jun 28 12:04:44 2019 from 190.187.64.106
[myuser@192.168.1.6 ~]$
```
Check:

* If local port (12345) is free, and the remote port had something listening on it.

* Check if It’s trying to bind on an IPv6 address, not IPv4. Solution: Force bind port to IPV4


```sh
$ ssh -4 -D 12345  myuser@192.168.1.6 -p222
```
To permanently disable IPv6, edit your ~/.ssh/config and add:


```sh
$ vi ~/.ssh/config
Host *
    AddressFamily inet

```
		
That will make sure SSH never even tries anything with IPv6.

