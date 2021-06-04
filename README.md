# MYSQL-SYSTEM-ADMINISTRATION

### GRANT USER PRIVILEGE ON DATABASE
```
SELECT User, Host FROM mysql.user; //check current user@host/localhost/ip
GRANT ALL PRIVILEGES ON databasename.* TO 'johndoe'@'10.20.20.%'; //set user privillege
```
### SHOW USERS
```
SELECT User, Host FROM mysql.user;
```
### CREATE NEW USER
```
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```
### SHOW DATABASES
```
SHOW DATABASES;
```
### SETUP MYSQL ROOT/USER PASSWORD
```
//If not work -new
$ sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'NEW_USER_PASSWORD';

//If not work -new
$sudo service mysql stop
$sudo mysqld_safe --skip-grant-tables&

UPDATE mysql.user SET authentication_string=null WHERE User='root';
mysql -u root
ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'yourpasswd';

//If not work above-old
mysql -u root -p
ALTER USER 'root'@'localhost' IDENTIFIED BY 'NEW_USER_PASSWORD';

//If not work above-old
UPDATE mysql.user SET authentication_string = PASSWORD('NEW_USER_PASSWORD')
WHERE User = 'root' AND Host = 'localhost';

//If not work above-old
$ mysqld --initialize-insecure
$ mysql -u root --skip-password
ALTER USER 'root'@'localhost' IDENTIFIED BY 'NEW_USER_PASSWORD';


```
