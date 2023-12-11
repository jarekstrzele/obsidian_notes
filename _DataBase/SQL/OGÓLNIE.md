12.07.2002
```shell 
mysql -u root -p
:Filozofia2!@
mysql> 
```
---

`docker run -it --name mysql_1 --detach -e MYSQL_ROOT_PASSWORD=Filozofia2 mysql `
potem 
`docker exec -it containerID mysql -u root -p`
(podaj haslo)

---------------
```javascript
import mysql.connector

my_db = mysql.connector.connect(
    host = "localhost",
    port = "8081",
    user = "root",
    password = "Filozofia2",
    # auth_plugin='mysql_native_password',
)

print(my_db)
```
ale trzeba od instalować mysql-connector i zainstalować 

```shell
mysql-connector-python
pip uninstall mysql-connector
pip uninstall mysql-connector-python
pip install mysql-connector-python
```

---------------------

dla kontenera: docker run -it --name mysql_1 --detach -e MYSQL_ROOT_PASSWORD=Filozofia2 -p 8081:3306 mysql 

import mysql.connector
my_db = mysql.connector.connect(
    host = "localhost",
    port = "8081",
    user = "root",
    password = "Filozofia2",
    # auth_plugin='mysql_native_password',

)


my_cur = my_db.cursor()
my_sql_create = "CREATE DATABASE testdb"
my_sql_show = "SHOW DATABASES"

my_cur.execute(my_sql_create)
my_cur.execute(my_sql_show)
for db in  my_cur:
    print(db)

print("done")

