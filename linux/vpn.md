<!-- TITLE: VPN -->
<!-- SUBTITLE: A quick summary of Vpn -->

# Verify:


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

# Errors
## STATE_QUICK_I1: retransmission; will wait 20s for response


```text
# ipsec auto --verbose --up myConn


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

## Solution

i finally got this working!!! one the other side, the third party had enabled pfs at their side, yet at my side i had disabled pfs, (pfs=no).. the third party have a cisco asa fw!, after disabling pfs, everything worked like charm, SA were established.. and would ping their LAN nodes behind the ASA fw!!