<!-- TITLE: VPN -->

# Diagram

![Vpnfortigate](/uploads/linux/vpnfortigate.png "Vpnfortigate")

# Verify


```text
[root@server]# ipsec verify
Verifying installed system and configuration files

Version check and ipsec on-path                         [OK]
Libreswan 3.23 (netkey) on 3.10.0-229.14.1.el7.x86_64
Checking for IPsec support in kernel                    [OK]
 NETKEY: Testing XFRM related proc values
         ICMP default/send_redirects                    [OK]
         ICMP default/accept_redirects                  [OK]
         XFRM larval drop                               [OK]
Pluto ipsec.conf syntax                                 [OK]
Two or more interfaces found, checking IP forwarding    [OK]
Checking rp_filter                                      [OK]
Checking that pluto is running                          [OK]
 Pluto listening for IKE on udp 500                     [OK]
 Pluto listening for IKE/NAT-T on udp 4500              [OK]
 Pluto ipsec.secret syntax                              [OK]
Checking 'ip' command                                   [OK]
Checking 'iptables' command                             [OK]
Checking 'prelink' command does not interfere with FIPS [OK]
Checking for obsolete ipsec.conf options                [OK]
[root@server]# 

```

# Conf

## Specs

### IKE Policy

Message Encryption algorithm: AES-256
Message integrity algorithm    : SHA-1
DH-Group                                : Group 2(1024 Bit)
IKE Lifetime                             : 86400 segs
Supports Aggressive Mode     : NO

### IPSec Parameters
Mechanism for payload encryption: AES-256
ESP Transform: SHA-1
Data Integrity: 3600s

### PFS

No PFS

## Host in (left) Fortigate Encription Domain:

10.10.10.64

## Secrets


```sh
cat  /etc/ipsec.d/myVpn.secrets

103.71.168.24 200.14.25.32 : PSK "apowerfullpassword"

```

## ipsec.conf

```sh
# /etc/ipsec.conf - Libreswan IPsec configuration file
#
# Manual:     ipsec.conf.5
version 2.0
config setup
        # Normally, pluto logs via syslog. If you want to log to a file,
        # specify below or to disable logging, eg for embedded systems, use
        # the file name /dev/null
        # Note: SElinux policies might prevent pluto writing to a log file at
        #       an unusual location.
        logfile=/var/log/pluto.log
        plutostderrlog=/var/log/pluto.error.log
        #
        # Do not enable debug options to debug configuration issues!
        #
        # plutodebug "all", "none" or a combation from below:
        # "raw crypt parsing emitting control controlmore kernel pfkey
        #  natt x509 dpd dns oppo oppoinfo private".
        # Note: "private" is not included with "all", as it can show confidential
        #       information. It must be specifically specified
        # examples:
        # plutodebug="control parsing"
        # plutodebug="all crypt"
        plutodebug=all
        # Again: only enable plutodebug when asked by a developer
        #plutodebug=none
        #nat_traversal=yes
        # NAT-TRAVERSAL support
        # exclude networks used on server side by adding %v4:!a.b.c.0/24
        # It seems that T-Mobile in the US and Rogers/Fido in Canada are
        # using 25/8 as "private" address space on their wireless networks.
        # This range has never been announced via BGP (at least up to 2015)
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:25.0.0.0/8,%v4:100.64.0.0/10,%v6:fd00::/8,%v6:fe80::/10
        #oe=off
        protostack=netkey
        #interfaces=%defaultroute
        #version 2.0
        #config setup
        #plutostderrlog="/var/log/ipsec_movis.log"
        #dumpdir=/var/run/pluto/
        #nat_traversal=yes
        #virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
        #oe=off
        #protostack=netkey
        #interfaces=%defaultroute

# fortigate vpn ipsec
conn elfortigate
        authby=secret
        auto=start
        pfs=no
        type=tunnel
        ### phase 1 ###
        ike=aes256-sha1;modp1024
        keylife=3600s
        ### phase 2 ###
        phase2=esp
        phase2alg=aes256-sha1;modp1024
        ikelifetime=86400s
        left=103.71.168.24  #Public IP
        leftsourceip=10.10.10.64
        leftsubnet=10.10.10.64/32
        leftnexthop=%defaultroute
        right=200.14.25.32 #Public IP
        rightsubnet=10.10.23.0/27
        #rightnexthop=%defaultroute

# For example connections, see your distribution's documentation directory,
# or https://libreswan.org/wiki/
#
# There is also a lot of information in the manual page, "man ipsec.conf"
#
# It is best to add your IPsec connections as separate files in /etc/ipsec.d/
#include /etc/ipsec.d/*.conf

```




# Errors
## STATE_QUICK_I1: retransmission; will wait 20s for response


```text
# ipsec auto --verbose --up elfortigate


104 "myConn" #281: STATE_MAIN_I1: initiate
003 "myConn" #281: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106
003 "myConn" #281: ignoring Vendor ID payload [FRAGMENTATION c0000000]
106 "myConn" #281: STATE_MAIN_I2: sent MI2, expecting MR2
003 "myConn" #281: received Vendor ID payload [Cisco-Unity]
003 "myConn" #281: received Vendor ID payload [XAUTH]
003 "myConn" #281: ignoring unknown Vendor ID payload [ad631e9af00364684d82c285fd11be28]
003 "myConn" #281: ignoring Vendor ID payload [Cisco VPN 3000 Series]
003 "myConn" #281: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: no NAT detected
108 "myConn" #281: STATE_MAIN_I3: sent MI3, expecting MR3
003 "myConn" #281: received Vendor ID payload [Dead Peer Detection]
004 "myConn" #281: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_128 prf=oakley_sha group=modp1024}
117 "myConn" #282: STATE_QUICK_I1: initiate
010 "myConn" #282: STATE_QUICK_I1: retransmission; will wait 20s for response
010 "myConn" #282: STATE_QUICK_I1: retransmission; will wait 40s for response

```

## Route table:


```text
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         gateway         0.0.0.0         UG    100    0        0 eth0
default         gateway         0.0.0.0         UG    101    0        0 eth1
10.10.23.0      gateway         255.255.255.224 UG    0      0        0 eth0

```

## Solution

i finally got this working!!! one the other side, the third party had enabled pfs at their side, yet at my side i had disabled pfs, (pfs=no).. the third party have a cisco asa fw!, after disabling pfs, everything worked like charm, SA were established.. and would ping their LAN nodes behind the ASA fw!!


# Taking traffic dumps on Linux (Capture outgoing and incomming packets across VPN):

The following rules use nflog group 5. Adjust the value for whatever group you're using.

ingress IPsec and IKE Traffic rule


```text
iptables -t raw -I PREROUTING -p esp -j NFLOG --nflog-group 5
iptables -t raw -I PREROUTING -p ah -j NFLOG --nflog-group 5
iptables -t raw -I PREROUTING -p udp -m multiport --dports 500,4500 -j NFLOG --nflog-group 5
```


egress IPsec and IKE traffic


```text
iptables -t raw -I OUTPUT -p esp -j NFLOG --nflog-group 5
iptables -t raw -I OUTPUT -p ah -j NFLOG --nflog-group 5
iptables -t raw -I OUTPUT -p udp -m multiport --dports 500,4500 -j NFLOG --nflog-group 5
```


decapsulated IPsec traffic


```text
iptables -t mangle -I PREROUTING -m policy --pol ipsec --dir in -j NFLOG --nflog-group 5
iptables -t mangle -I POSTROUTING -m policy --pol ipsec --dir out -j NFLOG --nflog-group 5
```


IPsec traffic that is destinated for the local host (iptables INPUT chain)


```text
iptables -t filter -I INPUT -m addrtype --dst-type LOCAL -m policy --pol ipsec --dir in -j NFLOG --nflog-group 5

```

IPsec traffic that is destinated for a remote host (iptables FORWARD chain)


```text
iptables -t filter -I FORWARD -m addrtype ! --dst-type LOCAL -m policy --pol ipsec --dir in -j NFLOG --nflog-group 5

```

IPsec traffic that is outgoing (iptables OUTPUT chain)


```text
iptables -t filter -I OUTPUT -m policy --pol ipsec --dir out -j NFLOG --nflog-group 5

```

Getting the traffic


```text
tcpdump -s 0 -n -i nflog:5

```

Ref: https://wiki.strongswan.org/projects/strongswan/wiki/CorrectTrafficDump
