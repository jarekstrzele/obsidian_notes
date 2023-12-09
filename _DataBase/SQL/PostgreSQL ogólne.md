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

aby zainstalować pgadmin4:
curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add
sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'

sudo apt install pgadmin4     ---- zainstaluje sporo paczek (też Apach2)
sudo /usr/pgadmin4/bin/setup-web.sh  (aby skonfigurtować (15.11.2021: js100code@gmail.com, Filozofia2!@
localhost/pgadmin4   -- zaloguj się

tworzenie użytkownika
`sudo -u postgres psql ` - uruchom użytkownika postrgres w terminalu psql

`alter user postgres with password 'postgres';`ustaw hasło użytkownika na postgres (uwaga na średnik na końcu)
`\q` - wyjście z terminala psql

>now run pgadmin: w terminalu napisz pgadmin4  -->>>> zamiast tego localhost/pgadmin4
server -> create-> ==user postgres==, ==hasło postgres==

15.11.2021: js100code@gmail.com, Filozofia2!@
dla servera postgres





