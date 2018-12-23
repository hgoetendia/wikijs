<!-- TITLE: Datetime -->
<!-- SUBTITLE: A quick summary of Datetime -->

# Date Class


```javascript
var dateToSend = new Date(); //Now

var sched_dd = dateToSend.getDate();
var sched_mm = dateToSend.getMonth() + 1; 
var sched_yyyy = dateToSend.getFullYear();
var sched_hour = dateToSend.getHours();
var sched_minute = dateToSend.getMinutes();
var sched_seconds = dateToSend.getSeconds();
var sched_date = `${sched_yyyy}-${sched_mm}-${sched_dd} ${sched_hour}:${sched_minute}:${sched_seconds}`;
```


Result:  `2018-12-23 14:30:20`


JavaScript ISO Dates

ISO 8601 is the international standard for the representation of dates and times.

The ISO 8601 syntax (YYYY-MM-DD) is also the preferred JavaScript date format:

Example (Complete date)


```javascript
var d = new Date("2015-03-25");
var e = new Date("2018-12-29T17:07:31.069Z");
```



