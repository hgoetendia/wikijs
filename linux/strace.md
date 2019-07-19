<!-- TITLE: Strace -->

# By Pid

-p = pid
-s = show strings with until 9024 chars


```text
sudo strace -p 1234 -s9024
```


# Java application

```text
sudo strace -F -p 1234
```

# To trace child process that's fork()ed.
```text
strace -f 
```
