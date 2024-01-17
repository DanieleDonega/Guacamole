After deploy containers:

docker run --rm guacamole/guacamole:1.5.4 /opt/guacamole/bin/initdb.sh --mysql > initdb.sql

docker cp initdb.sql guacamoledb:/initdb.sql

docker exec -it guacamoledb bash
cat /initdb.sql | mariadb -u root -p guacamole_db
exit
