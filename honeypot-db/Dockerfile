FROM mysql:5.7

RUN mkdir /usr/sql
RUN chmod 644 /usr/sql

RUN usermod -d /var/lib/mysql/ mysql

ADD ["mysql.sql", "/usr/sql"]

RUN service mysql start \
    && mysql -u root -p '' -e "CREATE DATABASE cowriedb" \
    && mysql -u root -p '' -e "GRANT ALL ON cowriedb.* TO \
    'cowrie'@'localhost' IDENTIFIED BY 'honey'" \
    && mysql -u root -p '' -e "FLUSH PRIVILEGES" \
    && cd /usr/sql \
    && mysql -u cowrie --password=honey cowriedb < mysql.sql \
    && cd / && rm -rd /usr/sql
