<!-- TITLE: SYN without SYN/ACK -->
<!-- SUBTITLE: Setting for a webserver with big transactionality -->



Change the `net.ipv4.tcp_tw_recycle` parameter from 1 to 0


```sh
sudo sysctl -w net.ipv4.tcp_tw_recycle=0
```

Or

```sh
sudo echo 0 > /proc/sys/net/ipv4/tcp_tw_recycle
```

For making changes permanetly  edit `/etc/sysctl.conf`


```text
#net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_tw_recycle = 0
```
