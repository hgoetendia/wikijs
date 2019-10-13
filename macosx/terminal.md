<!-- TITLE: Terminal -->
# Errors

## LC_CTYPE: cannot change locale (UTF-8): No such file or directory


```text
[user@MBA:~]$ ssh user@server.com
user@server.com's password:
Last login: Sat Oct 12 23:21:16 2019 from 179.6.205.232
-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory
[test@server:~]$
```

### Solution 1

```text
If you are using the ‘Terminal’ app then click on

Terminal > Preferences > Select Terminal type such as Basic (default) > Advanced tab
Make sure that the ‘Set locale environment variables on startup’ is unchecked as follows:
```

![Screen Shot 2016 09 11 At 1 46 38 Pm](/uploads/others/screen-shot-2016-09-11-at-1-46-38-pm.png "Screen Shot 2016 09 11 At 1 46 38 Pm")

### Solution 2

Preventing OpenSSH Client from sending the LC_* variables on OS X / Linux / Unix desktop

Edit /etc/ssh/ssh_config or /etc/ssh_config file, enter:


```text
$ sudo vi ~/.ssh/config

```

Remove or comment out as follows:

```text
#SendEnv LANG LC_*
```


Save and close the file.

### Solution 3

Install required locale on the remote server

Finally, you can fix this problem either installing the desired locale using the localedef command, or consider choosing a different locale in locale/remote system:


```text
# localedef -i en_US -f UTF-8 en_US.UTF-8

```

Ref:

https://www.cyberciti.biz/faq/os-x-terminal-bash-warning-setlocale-lc_ctype-cannot-change-locale/