<!-- TITLE: Linux/Timezone -->

# Set up the timezone.

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
             Local time: Wed 2018-06-20 12:37:55 -05
    Universal time: Wed 2018-06-20 17:37:55 UTC
                 RTC time: Wed 2018-06-20 17:37:55
               Time zone: America/Lima (-05, -0500)
           NTP enabled: yes
NTP synchronized: yes
  RTC in local TZ: no
             DST active: n/a
```
 