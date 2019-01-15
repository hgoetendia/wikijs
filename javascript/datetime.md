<!-- TITLE: JavaScript: Date and time -->

# Date Class


```javascript
var dateToSend = new Date(); //Now

var sched_dd = dateToSend.getDate();
var sched_mm = dateToSend.getMonth() + 1;  //Months are from 0 to 11
var sched_yyyy = dateToSend.getFullYear();
var sched_hour = dateToSend.getHours();
var sched_minute = dateToSend.getMinutes();
var sched_seconds = dateToSend.getSeconds();
var sched_date = `${sched_yyyy}-${sched_mm}-${sched_dd} ${sched_hour}:${sched_minute}:${sched_seconds}`;
```


Sample `sched_date` result:  `2018-12-23 14:30:20`


JavaScript ISO Dates

ISO 8601 is the international standard for the representation of dates and times.

The ISO 8601 syntax (YYYY-MM-DD) is also the preferred JavaScript date format

ISO dates can be written with added hours, minutes, and seconds (YYYY-MM-DDTHH:MM:SSZ)

Date and time is separated with a capital T,  UTC time is defined with a capital letter Z.

If you want to modify the time relative to UTC, remove the Z and add +HH:MM or -HH:MM instead

Examples

```javascript
var d = new Date("2019-01-01");// Result: Mon Dec 31 2018 19:00:00 GMT-0500 (Peru Standard Time)
var e = new Date(2019, 1, 0); // Thu Jan 31 2019 00:00:00 GMT-0500 (Peru Standard Time)
var f = new Date("2018-12-29T17:07:31.069Z");
var g = new Date("2015-03-25T12:00:00-06:30"); 
```



