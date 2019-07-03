<!-- TITLE: Replication -->
<!-- SUBTITLE: A quick summary of Replication -->

# In master:
* Get tablespace location

```text
[local] postgres=# \db+                                     
                                        Listado de tablespaces      
    Nombre    |  Dueño   |         Ubicación          | Privilegios | Opciones | Tamaño  | Descripción                                  
--------------+----------+----------------------------+-------------+----------+---------+-------------                                 
 pg_default   | postgres |                            |             |          | 14 GB   |                                              
 pg_global    | postgres |                            |             |          | 3512 kB |                                              
 zbsmsco_hist | zbsmsco  | /d_historicos/mydirectory  |             |          | 156 GB  |                                              
 zbsmsco_idx  | zbsmsco  | /db_data2/other_directory  |             |          | 17 GB   |  
```

* Get database data directort


```text
postgres  7229  0.0  0.6 8815184 209188 ?      S     2018 304:10 /usr/pgsql-9.5/bin/postgres -D /db_data1/pgsql/9.5/data
```



```pgsql
postgres=# select pg_start_backup('mylabel_reload');
          pg_start_backup 
-----------------
 575/B8000028
(1 fila)

Duración: 784268,748 ms
[local] postgres@postgres=# 
```



In shell


```sh
rsync -avz /d_historicos/mydirectory/ postgres@172.16.0.100:/d_historicos/mydirectory/
rsync -avz /db_data2/other_directory/ postgres@172.16.0.100:/db_data2/other_directory/
rsync -avz /db_data1/pgsql/9.5/data postgres@172.16.0.100:/db_data1/pgsql/9.5/

```



```pgsql
postgres=# select pg_stop_backup();
```


