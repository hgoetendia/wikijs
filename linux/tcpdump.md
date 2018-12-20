<!-- TITLE: Tcpdump -->
<!-- SUBTITLE: A quick summary of Tcpdump -->

-w myfile.pcap  # Dump to file myfile.pcap
-ieth0                 # eth0 interface, if you want any -iany
                   

# By Port


```text

```



```sh
tcpdump -Zroot -U -ieth0 -s3000 -w myfile.pcap -C20 "port 5563 or port 15562"
```
