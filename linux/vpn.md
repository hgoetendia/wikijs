<!-- TITLE: VPN -->
<!-- SUBTITLE: A quick summary of Vpn -->

# Errors
## STATE_QUICK_I1: retransmission; will wait 20s for response


```text
# ipsec auto --up myConn

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