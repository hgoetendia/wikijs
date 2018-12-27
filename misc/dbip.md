<!-- TITLE: DB-IP -->
<!-- SUBTITLE: Service to obtain a location from IP using https://db-ip.com service-->

# Get IP location 
SQL sentence to get IP's geolocation:

## MySQL
IPV4 

```sql
SELECT 
	* 
FROM 
	dbip_lookup 
WHERE 
	addr_type = 'ipv4' AND  
	ip_start <= unhex(CONV(INET_ATON('190.187.64.106'),10,16))  
ORDER BY 
	ip_start 
DESC LIMIT 1;
```
