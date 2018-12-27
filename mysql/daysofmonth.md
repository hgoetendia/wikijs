<!-- TITLE: MySQL/List days of current month -->


```sql
SELECT s.start_date + INTERVAL (days.d) DAY  AS my_date FROM ( SELECT LAST_DAY(CURRENT_DATE) + INTERVAL 1 DAY - INTERVAL 1 MONTH  AS start_date, LAST_DAY(CURRENT_DATE) AS end_date ) AS s JOIN days ON  days.d <= DATEDIFF(s.end_date, s.start_date) ;
```

Output:


```text
+------------+
| my_date    |
+------------+
| 2018-12-01 |
| 2018-12-02 |
| 2018-12-03 |
| 2018-12-04 |
| 2018-12-05 |
| 2018-12-06 |
| 2018-12-07 |
| 2018-12-08 |
| 2018-12-09 |
| 2018-12-10 |
| 2018-12-11 |
| 2018-12-12 |
| 2018-12-13 |
| 2018-12-14 |
| 2018-12-15 |
| 2018-12-16 |
| 2018-12-17 |
| 2018-12-18 |
| 2018-12-19 |
| 2018-12-20 |
| 2018-12-21 |
| 2018-12-22 |
| 2018-12-23 |
| 2018-12-24 |
| 2018-12-25 |
| 2018-12-26 |
| 2018-12-27 |
| 2018-12-28 |
| 2018-12-29 |
| 2018-12-30 |
| 2018-12-31 |
+------------+
```


