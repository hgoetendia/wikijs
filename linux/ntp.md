<!-- TITLE: NTP -->

# NTP Client

Port 123/UDP.

## Printing or querying date (not set the time)

### ntpdate
```sh
ntpdate -q pool.ntp.org
```

The -q switch says to query only and not set the time. With this command you can query an NTP server and it will return the date it has set.

### rdate

```sh
rdate -p pool.ntp.org
```

-p     Print the time returned by the remote machine.


## Setting time

### rdate
```sh
sudo /usr/bin/rdate -s pool.ntp.org
sudo /sbin/hwclock --systohc --utc
```
### ntpdate

```sh
sudo /usr/sbin/ntpdate -u pool.ntp.org
sudo /sbin/hwclock --systohc --utc
```
