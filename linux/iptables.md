<!-- TITLE: Iptables -->

# Show rules

## List Rules by Specification

```sh
sudo iptables -S
```

## List specific chain
```sh
sudo iptables -S TCP
```
## List rules as tables
```sh
sudo iptables -L
```
```sh
sudo iptables -L INPUT
```

## List NAT rules


```text
[root@server ]# iptables -t nat -L --line-numbers
Chain PREROUTING (policy ACCEPT)
num  target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         


Chain POSTROUTING (policy ACCEPT)
num  target     prot opt source               destination         
1    SNAT       all  --  anywhere             anywhere             to:110.33.255.132
```


## Remove iptables POSTROUTING NAT rule


```text
[root@server ]# iptables -t nat -D POSTROUTING 1

```




