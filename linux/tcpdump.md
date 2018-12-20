<!-- TITLE: Tcpdump -->
<!-- SUBTITLE: A quick summary of Tcpdump -->

# By Port

```sh
tcpdump -Zroot -U -ieth0 -s3000 -w myfile.pcap -C20 "port 5563 or port 15562"
```
