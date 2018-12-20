<!-- TITLE: Tcpdump -->
<!-- SUBTITLE: A quick summary of Tcpdump -->

* -w myfile.pcap  # Dump to file myfile.pcap
* -ieth0                 # eth0 interface,  -iany, -il0
                   
# By Port

```sh
tcpdump -Zroot -U -ieth0 -s3000 -w myfile.pcap -C20 "port 5563 or port 15562"
```

# Variable dump file 
```sh
tcpdump -Zroot -s2000 -G60 -ieth0 "port 1155 or port 2020" -wSOMETHING_201804.%F_%T_pcap 
```