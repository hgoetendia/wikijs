<!-- TITLE: SYN without SYN/ACK -->
<!-- SUBTITLE: Setting for a webserver with big transactionality -->

Reference: https://serverfault.com/questions/235965/why-would-a-server-not-send-a-syn-ack-packet-in-response-to-a-syn-packet


Disable the parameter changing the `net.ipv4.tcp_tw_recycle` parameter from 1 to 0

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



### The opposite effect

Enabling these tunables will not make the host crash or unstable, but it may break TCP/IP functionality if the host is connected to devices such as load-balancers or firewalls.  Some of these devices can reject SYN if it reuses the same connection (i.e. src/dst IP and src/dst ports are the same) too quickly.  RFC 1122 describes when it is acceptable to recycle the connection when SYN arrives for a connection in TIME_WAIT state. 

The problem (if any) will manifest itself as establishment / termination of some connections that are working incorrectly, for example when initial negotiation fails unexpectedly or when a connection does not close properly. 

Setting tcp_tw_recycle to 1 makes a Linux host drop TIME_WAIT connections much faster.  Instead of a predefined 2*MSL period of 60s, the host will use a timeout based on RTT estimate.  For LANs, it is usually several milliseconds.

Setting tcp_tw_reuse to 1 will make a host reuse the same connection quickly for outgoing connections. 

As the documentation says, it is better to consult networking resources to see whether enabling these options makes sense for your environment.

Reference: https://support.hpe.com/hpsc/doc/public/display?docId=emr_na-c00916755
