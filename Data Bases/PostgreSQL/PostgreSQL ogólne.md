[[_ intro sql postgresql]]

---

https://www.tecmint.com/install-postgresql-and-pgadmin-in-ubuntu/   (tu są informacje jak zinstalować pgadmin4

09.11.2021:
	http://127.0.0.1/pgadmin4
	jarek
	Filozofia2!@
	js100code@gmail.com
-------------------------------------------------------
https://www.postgresql.org/download/linux/ubuntu/
`sudo systemctl start postgresql`
`sudo systemctl enable postgresql` -- gdy system będzie się włączał postgre też

> [!important]
>  `sudo passwd postgres` to set a password for a postgres user

# PGAdmin4
aby zainstalować pgadmin4:
1. add pgAdmin4 repo to ubuntu
`curl  -fsSL https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/pgadmin.gpg`
and next:
`sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list'`

2. install pgAdmin4
`sudo apt update`
`sudo apt install pgadmin4`

check if the apache service have been started:
`systemctl status apache2`

3. configure apache web server for pgAdmin4
`sudo /usr/pgadmin4/bin/setup-web.sh`
(26.08 js100code@gmail.com, Filozofia2!@)

4. access pgAdmin4 Web Interface
`sudo ufw allow http`
`sudo ufw allow https`

`http://localhost/pgadmin4`
or pgAdmin4 app

### tworzenie użytkownika
`sudo -u postgres psql ` - uruchom użytkownika postrgres w terminalu psql

`alter user postgres with password 'postgres';`ustaw hasło użytkownika na postgres (uwaga na średnik na końcu)
`\q` - wyjście z terminala psql

>now run pgadmin: w terminalu napisz pgadmin4  -->>>> zamiast tego localhost/pgadmin4
server -> create-> ==user postgres==, ==hasło postgres==

PGAdmin4
16.08.2022
js100code@gmail.com
Filozofia2!@
 http://127.0.0.1/pgadmin4

https://www.youtube.com/watch?v=d5v5Ze_Wvus
postgres
Filozofia2



