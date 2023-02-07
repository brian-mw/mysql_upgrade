## MYSQL 5.6 to 8 UPGRADE GUIDE
- This guide will provide a step-by-step overview of the process to upgrade from MySQL 5.6 to 8.0, and help you to ensure a smooth transition while preserving your existing data and configurations.
  
NB: 
 - It is required to upgrade from 5.6 to 5.7 first, then 5.7 to 8.0. Doing an upgrade that skips version is not supported (https://dev.mysql.com/doc/refman/8.0/en/upgrade-paths.html)
 - You should ensure that you have at least 2 GB free
## Steps
- Clone the repository

### Upgrading to mysql 5.7
- stop current running mysql instance ``sudo service mysql stop``
- navigate into the mysql5.7 folder ``cd mysql5.7``
- install the rest of the packages ``sudo dpkg -i *.deb``
- create a symbolic link to connect mysql through socket ``ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock``
- start mysql service ``sudo service mysql start``
- run mysql upgrade script to update all table definitions ``mysql_upgrade -u root -p``
- repair any broken indexes on the tables in your database ``mysqlcheck -u root --auto-repair --all-databases``

### Upgrading to mysql 8

- stop current running mysql instance ``sudo service mysql stop``
- navigate into the mysql5.7 folder ``cd mysql8``
- install the rest of the packages ``sudo dpkg -i *.deb``
- start mysql service ``sudo service mysql start``

### Troubleshooting