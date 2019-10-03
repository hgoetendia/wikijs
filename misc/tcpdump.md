<!-- TITLE: Tcpdump -->

* -w myfile.pcap  #  Dump to file myfile.pcap
* -ieth0                 # eth0 interface,  -iany, -il0
* -C20                  # Dump file will rotate every 1000000 bytes (not 1048576 bytes), for the example aprox 20MB.
* -s3000               # snapshot length (snap len) in bytes, no more than snaplen bytes of each network packet will be read into memory, or saved to disk.  A value of 0 specifies a snapshot length of 65535, so that the full packet is captured; this is the default.
* -Zroot                # Drops privileges (if root) and changes user ID to user and the group ID to the primary group of user.
# By Port

```sh
tcpdump -Zroot -U -ieth0 -s3000 -w myfile.pcap -C20 "port 5563 or port 15562"
```


# Variable dump file 
* -G60  # Dump file will rotate every 60 seconds, savefiles will have the name specified by -w which should include a time format as defined by strftime(3).  If no time format is specified, each new file will overwrite the previous.

```sh
tcpdump -Zroot -s2000 -G60 -ieth0 "port 1155 or port 2020" -wSOMETHING_201804.%F_%T_pcap 
```


# HTTP POST/GET Request / Response
Change ens192 to right network interface and 80 to specific port.

```sh
tcpdump  -s 0 -i ens192 -A 'tcp dst port 80 and tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420 or tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x504F5354 or tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x48545450 or tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x3C21444F'
```

# Show TCP SYN/ACK packets - each established TCP conversation excluding localhost:

By selecting on the tcp-syn and tcp-fin packets we can show each established TCP conversation with timestamps but without the data. As with many filters this allows the amount of noise to be reduced in order to focus in on the information that you care about.

-nn  Do not convert protocol names.

```sh
tcpdump -nn -ieth0 'tcp[tcpflags] & (tcp-syn|tcp-fin) != 0 and not src and dst net 127.0.0.1'
```

# Customizing output dump file:

Args:

```text
-G Rotate_seconds
-s Snarf  snaplen bytes of data from each packet rather than the default of 65535 bytes.  Packets truncated because of a limited snapshot are indicated in the output with ‘‘[|proto]’’, where proto is the name of the protocol level at which the truncation has occurred
```

Command:

```sh
sudo tcpdump -s2000 -G60 -ieth0 port 20120 -wHelloWorld_%F_%T_pcap -Zroot

```

Output:


```text
HelloWorld_2019-08-05_15:29:41_pcap

```

# Capture ICMP packets


```sh
/usr/sbin/tcpdump -iany -n icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode                                             
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes                                                  
10:54:40.620156 IP 10.10.10.72 > 10.10.10.25: ICMP echo request, id 30327, seq 117, length 64
10:54:40.620238 IP 10.10.10.25 > 10.10.10.72: ICMP echo reply, id 30327, seq 117, length 64
10:54:41.620551 IP 10.10.10.72 > 10.10.10.25: ICMP echo request, id 30327, seq 118, length 64
10:54:41.620551 IP 10.10.10.25 > 10.10.10.72: ICMP echo reply, id 30327, seq 118, length 64
10:54:42.622551 IP 10.10.10.72 > 10.10.10.25: ICMP echo request, id 30327, seq 119, length 64
10:54:42.622551 IP 10.10.10.25 > 10.10.10.72: ICMP echo reply, id 30327, seq 119, length 64
10:54:43.621927 IP 10.10.10.72 > 10.10.10.25: ICMP echo request, id 30327, seq 120, length 64
10:54:43.621949 IP 10.10.10.25 > 10.10.10.72: ICMP echo reply, id 30327, seq 120, length 64
8 packets captured                                         
8 packets received by filter                               
0 packets dropped by kernel                                

```



