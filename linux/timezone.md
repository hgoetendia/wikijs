<!-- TITLE: Linux/Timezone -->

# Set up timezone.

```sh
timedatectl list-timezones
```

Choose one for example America/Lima

```sh
sudo timedatectl set-timezone 'America/Lima'
```

 For checking
 
 ```sh
timedatectl 
      Local time: jue 2018-12-20 11:08:14 -05
  Universal time: jue 2018-12-20 16:08:14 UTC
        RTC time: jue 2018-12-20 16:08:14
       Time zone: America/Lima (-05, -0500)
     NTP enabled: yes
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a
```

> In this stage if you restart you will lost your date time settings.

 # Configure NTP Synchronization
 

```sh
sudo yum install ntp
sudo systemctl start ntpd
sudo systemctl enable ntpd
```

> In this stage your changes will be permanetly


# Alternative to setup timezone

```sh
sudo mv /etc/localtime /etc/localtime.bak
sudo ln -s /usr/share/zoneinfo/America/Lima /etc/localtime
```
