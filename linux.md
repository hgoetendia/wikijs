<!-- TITLE: Linux -->

# Misc
* [Setup time and timezone](/linux/timezone)
* [Strace](/linux/strace)
* [Users](/linux/users)

# Tricks

* [Delete specific line number(s) from a text file](/linux/deletelinesfromfile)
* [Replace characters to others](/linux/replacecharacterstoothers)

# Tunning
* [SYN without SYN/ACK response](/tcpip/synwithoutsynack)

# NTP

## Printing or querying date (not set the time)

```sh
ntpdate -q pool.ntp.org
```

The -q switch says to query only and not set the time. With this command you can query an NTP server and it will return the date it has set.

```sh
rdate -p pool.ntp.org
```

-p     Print the time returned by the remote machine.

