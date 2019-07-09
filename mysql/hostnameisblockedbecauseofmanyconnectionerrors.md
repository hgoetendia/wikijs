<!-- TITLE: Host ‘host_name’ is blocked because of many connection errors -->

# Host ‘host_name’ is blocked because of many connection errors.

Unblock with ‘mysqladmin flush-hosts’
La solución está clara, acceder al servidor MySQL y ejecutar el comando siguiente como root:


```sh
$ mysqladmin flush-hosts

```

o en la consola del mysql ejecutar: 


```text
mysql> flush hosts;

```

El origen del problema es que el servidor MySQL ha recibido demasiados intentos de conexión desde la máquina indicada que han sido interrumpidos. Este tipo de conexiones fallidas provocan que el servidor MySQL detecte indicios de actividad sospechosa desde el host que está generando los errores, y por seguridad decide bloquearle el acceso.

Por defecto, Mysql está configurado para permitir 10 conexiones incorrectas antes de bloquearlo, si queremos ampliar este número deberemos reconfigurar la siguiente variables en nuestro fichero de configuración (my.cnf):


```text
max_connect_errors= xxxx
```


Lo recomendable de todas formas es detectar el origen del problema para evitar tener que modificar un parámetro como este que puede afectar a la seguridad de nuestro sistema, analizar el origen de estas conexiones, el porqué de los fallos, etc.