
# MariaDB - PostgreSQL en Linux

## Instalar MariaDB debian


* :link: [MariaDB Downloads](https://downloads.mariadb.org/mariadb/repositories/#mirror=globotech)

Crear en `source.list`

```
# MariaDB 10.2 repository list - created 2018-04-30 01:28 UTC
# http://downloads.mariadb.org/mariadb/repositories/
deb [arch=amd64,i386,ppc64el] http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.2/debian stretch main
deb-src http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.2/debian stretch main

```
Despues

```
sudo apt-get install software-properties-common dirmngr
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xF1656F24C74CD1D8
sudo apt-get update
sudo apt-get install mariadb-server
```


## Instalar PostgreSql :link: https://www.postgresql.org/

En debian 9

Añadir en el archivo `/etc/apt/sources.list`
```
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
```

Importar la key
```
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```

Para que quede de la siguiente mandera:
```
# PostgreSQL
deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main
# wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
# apt-get install postgresql postgresql-client postgresql-contrib libpq-dev
```

### Howto's MySql

Mostrar lista de todos usuarios de MySql
```
mysql> SELECT user,host FROM mysql.user;
```

Mostrar privilegios concedidos de un usuario
```
mysql> show grants for 'root'@'%';
SHOW GRANTS FOR 'root'@'localhost';
```

Muestra las BD
```
mysql> show DATABASES;
```

Crea una BD
```
mysql> CREATE DATABASE nombredelabasededatos;
```

Borrar una BD
```
mysql> DROP DATABASE nombredelabasededatos;
```

Para usar una BD
```
mysql> USE nombredelabasededatos;
```

Para borrar un usuario.
```
mysql> DROP USER 'usuario';
```

Para mostrar las tablas:
```
mysql> SHOW TABLES;
```

Crear usuario
```
mysql> CREATE USER 'mi_usuario'@'localhost' IDENTIFIED BY 'mi_contraseña';
```

Para dar permisos desde la consola sobre todas las tablas de una base de datos
```
mysql> GRANT ALL PRIVILEGES ON nombredelabasededatos.* TO 'landani'@'localhost';
```

Después de dar o quitar permisos, siempre tendremos que ejecutar el siguiente comando para aplicarlos.
```
mysql> FLUSH PRIVILEGES;
```

Para dar permisos desde la consola sobre una tabla concreta de la base de datos
```
mysql> GRANT SELECT,INSERT,UPDATE,DELETE ON database_name.concrete_table TO 'landani'@'%';
```

Para quitar permisos desde la consola de mysql, ejecutaremos el siguiente comando. Si queremos afectar a una base de datos, tabla concreta, etc. lo haremos igual que para dar permisos. En este ejemplo afectamos a todas las bases de datos *(*.*)* y quitaremos todos los permisos (`ALL PRIVILEGES`)
```
mysql> REVOKE ALL PRIVILEGES ON *.* FROM 'landani'@'localhost';
```

Para saber que BD estoy usando.
```
mysql> SELECT DATABASE(); ------- \s
```

Para saber que usuario estoy parado.
```
mysql> SELECT USER(); ------- \s
mysql> SELECT CURRENT_USER;
```

Para saber los privilegios de un usuario.
```
mysql> SHOW GRANTS FOR 'root'@'localhost';
```

Para ver los privilegios consedidos a una cuenta que se esta que se esta usuando conectada al server
```
SHOW GRANTS;
SHOW GRANTS FOR CURRENT_USER;
SHOW GRANTS FOR CURRENT_USER();
```

How to check MySQL Server is running?
```
# mysqladmin -u root -p ping

    Enter password:
    mysqld is alive
```

How to Check which MySQL version I am running?
```
# mysqladmin -u root -p version
```

How to Find out current Status of MySQL server?
```
# mysqladmin -u root -ptmppassword status
```

How to check status of all MySQL Server Variable’s and value’s?
```
# mysqladmin -u root -p extended-status   
```

How to see all MySQL server Variables and Values?
```
# mysqladmin  -u root -p variables
```

How to check all the running Process of MySQL server?
```
# mysqladmin -u root -p processlist
```

How to reload/refresh MySQL Privileges?
```
# mysqladmin -u root -p reload;
# mysqladmin -u root -p refresh
```

Como apagar el servidor de MySql dse forma segura
```
# mysqladmin -u root -p shutdown
    Ó
# /etc/init.d/mysqld stop
# /etc/init.d/mysqld start
```

Some useful MySQL Flush commands - Following are some useful flush commands with their description.
```
flush-hosts: Flush all host information from host cache.
flush-tables: Flush all tables.
flush-threads: Flush all threads cache.
flush-logs: Flush all information logs.
flush-privileges: Reload the grant tables (same as reload).
flush-status: Clear status variables.

# mysqladmin -u root -p flush-hosts
# mysqladmin -u root -p flush-tables
# mysqladmin -u root -p flush-threads
# mysqladmin -u root -p flush-logs
# mysqladmin -u root -p flush-privileges
# mysqladmin -u root -p flush-status
```

How to kill Sleeping MySQL Client Process? - Use the following command to identify sleeping MySQL client process.
```
# mysqladmin -u root -p processlist
```

Despues con el siguiente comando se mata el proceso, es el "Id"
```
# mysqladmin -u root -p kill 5
```

How to Connect remote mysql server - To connect remote MySQL server, use the -h (host)  with IP Address of remote machine.
```
# mysqladmin  -h 172.16.25.126 -u root -p
```

How to start/stop MySQL replication on a slave server? - To start/stop MySQL replication on salve server, use the following commands.
```
# mysqladmin  -u root -p start-slave
# mysqladmin  -u root -p stop-slave
```

How to store MySQL server Debug Information to logs? - It tells the server to write debug information about locks in use, used memory and query usage to the MySQL log file including information about event scheduler.
```
# mysqladmin  -u root -p debug
```
