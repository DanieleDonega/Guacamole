1)Install Mysql

2)Open and edit /etc/my.cnf or /etc/mysql/my.cnf, depending on your distribution.
3)Add skip-grant-tables under [mysqld]
4)Restart MySQL (sudo /etc/init.d/mysql restart)

5)cd guacamole/etc/extensions/wget https://github.com/DanieleDonega/Guacamole/blob/main/guacamole-auth-radius-1.5.3.jar
6)create guacamole.properties on guacamole/etc/

After deploy containers:

docker run --rm guacamole/guacamole:1.5.4 /opt/guacamole/bin/initdb.sh --mysql > initdb.sql

docker cp initdb.sql guacamoledb:/initdb.sql

docker exec -it guacamoledb bash
cat /initdb.sql | mysql -u root -p guacamole_db (passwowd MYSQL_ROOT_PASSWORD)
exit

restart docker
