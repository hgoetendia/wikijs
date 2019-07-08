<!-- TITLE: Haproxy -->

# Proxy TCP socket to forward to another IP/PORT

IP to forward 3307 to 192.168.0.83:3306 


```text
#---------------------------------------------------------------------
# Example configuration for a possible web application.  See the
# full configuration options online.
#
#   http://haproxy.1wt.eu/download/1.4/doc/configuration.txt
#
#---------------------------------------------------------------------

#---------------------------------------------------------------------
# Global settings
#---------------------------------------------------------------------
global
    # to have these messages end up in /var/log/haproxy.log you will
    # need to:
    #
    # 1) configure syslog to accept network log events.  This is done
    #    by adding the '-r' option to the SYSLOGD_OPTIONS in
    #    /etc/sysconfig/syslog
    #
    # 2) configure local2 events to go to the /var/log/haproxy.log
    #   file. A line like the following can be added to
    #   /etc/sysconfig/syslog
    #
    #    local2.*                       /var/log/haproxy.log
    #
    log         127.0.0.1 local2

    chroot      /var/lib/haproxy
    pidfile     /var/run/haproxy.pid
    maxconn     4000
    user        haproxy
    group       haproxy
    daemon

    # turn on stats unix socket
    stats socket /var/lib/haproxy/stats

#---------------------------------------------------------------------
# common defaults that all the 'listen' and 'backend' sections will
# use if not designated in their block
#---------------------------------------------------------------------
defaults
    mode                    tcp
    log                     global
    option                  dontlognull
    option                  redispatch
    retries                 3
    timeout http-request    10s
    timeout queue           1m
    timeout connect         10s
    timeout client          1m
    timeout server          1m
    timeout check           10s
    maxconn                 3000


listen  main
    bind :3307
    default_backend             app


#---------------------------------------------------------------------
# round robin balancing between the various backends
#---------------------------------------------------------------------
backend app
    server  app0 192.168.0.83:3306 check

##Monitor haproxy
listen stats # Define a listen section called "stats"
 bind :8999 # Listen on localhost:8999
 mode http
 stats enable  # Enable stats page
 stats hide-version  # Hide HAProxy version
 stats realm Haproxy\ Statistics  # Title text for popup window
 stats uri /haproxy_stats  # Stats URI
 stats auth haproxy:haproxy123  # Authentication credentials

```

Lauching haproxy


```sh
./haproxy -D -f myhaproxy.cfg

```


# Proxy TCP socket to charge balance

Port to balance localhost:8080  across 8000, 8001, 8002, 8003, 8004


Config file named: myhaproxy.cfg

```text
#---------------------------------------------------------------------
# Example configuration for a possible web application.  See the
# full configuration options online.
#
#   http://haproxy.1wt.eu/download/1.4/doc/configuration.txt
#
#---------------------------------------------------------------------

#---------------------------------------------------------------------
# Global settings
#---------------------------------------------------------------------
global
    # to have these messages end up in /var/log/haproxy.log you will
    # need to:
    #
    # 1) configure syslog to accept network log events.  This is done
    #    by adding the '-r' option to the SYSLOGD_OPTIONS in
    #    /etc/sysconfig/syslog
    #
    # 2) configure local2 events to go to the /var/log/haproxy.log
    #   file. A line like the following can be added to
    #   /etc/sysconfig/syslog
    #
    #    local2.*                       /var/log/haproxy.log
    #
    log         127.0.0.1 local2

    chroot      /var/lib/haproxy
    pidfile     /var/run/haproxy.pid
    maxconn     4000
    user        haproxy
    group       haproxy
    daemon

    # turn on stats unix socket
    stats socket /var/lib/haproxy/stats

#---------------------------------------------------------------------
# common defaults that all the 'listen' and 'backend' sections will
# use if not designated in their block
#---------------------------------------------------------------------
defaults
    mode                    tcp
    log                     global
    option                  dontlognull
    option                  redispatch
    retries                 3
    timeout http-request    10s
    timeout queue           1m
    timeout connect         10s
    timeout client          1m
    timeout server          1m
    timeout check           10s
    maxconn                 3000


listen  main 
    bind :8080
    default_backend             app


#---------------------------------------------------------------------
# round robin balancing between the various backends
#---------------------------------------------------------------------
backend app
    balance     roundrobin
    server  app0 127.0.0.1:8000 check
    server  app1 127.0.0.1:8001 check
    server  app2 127.0.0.1:8002 check
    server  app3 127.0.0.1:8003 check

##Monitor haproxy
listen stats # Define a listen section called "stats"
 bind :8999 # Listen on localhost:8999
 mode http
 stats enable  # Enable stats page
 stats hide-version  # Hide HAProxy version
 stats realm Haproxy\ Statistics  # Title text for popup window
 stats uri /haproxy_stats  # Stats URI
 stats auth haproxy:haproxy123  # Authentication credentials


```

Launching haproxy

```sh
./haproxy -D -f myhaproxy.cfg
```
