<!-- TITLE: UDP server client -->

# UDP server

Example port 3671


```perl
#!/usr/bin/perl

use strict;
use warnings;

use IO::Socket::INET;

# Send data immediately without buffering
$| = 1;

my ($socket,$data);

#  Create a new UDP socket
$socket = new IO::Socket::INET (
    LocalPort => 3671,
    Proto        => 'udp'
) or die "ERROR creating socket : $!\n";

my ($datagram,$flags);
while (1) {
    $socket->recv($datagram,42,$flags);
    print "Received datagram from ", $socket->peerhost,
                  ", flags ", $flags || "none", ": $datagram\n";
}

$socket->close();

```

# UDP client
* Server IP:PORT 192.168.1.1:3671

```perl
#!/usr/bin/perl -w
use strict;
use IO::Socket::INET;
my $sock = new IO::Socket::INET(PeerAddr => '192.168.1.1',
                PeerPort => 3671,
                Proto => 'udp', Timeout => 1) or die('Error opening socket.');
my $data = "hello";
print $sock $data;
```

