1)Install Mysql

2)Open and edit /etc/my.cnf or /etc/mysql/my.cnf, depending on your distribution.
Add skip-grant-tables under [mysqld]
Restart MySQL (sudo /etc/init.d/mysql restart)


After deploy containers:

docker run --rm guacamole/guacamole:1.5.4 /opt/guacamole/bin/initdb.sh --mysql > initdb.sql

docker cp initdb.sql guacamoledb:/initdb.sql

docker exec -it guacamoledb bash
cat /initdb.sql | mysql -u root -p guacamole_db (passwowd MYSQL_ROOT_PASSWORD)
exit
