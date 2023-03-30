# How-To-Install-MySQL-on-Ubuntu-20.04
MySQL is an open-source database management system, commonly installed as part of the popular LAMP (Linux, Apache, MySQL, PHP/Python/Perl) stack. It implements the relational model and uses Structured Query Language (better known as SQL) to manage its data.

## Step 1 — Installing MySQL
```
sudo apt update
sudo apt install mysql-server
sudo systemctl start mysql.service
```
These commands will install and start MySQL, but will not prompt you to set a password or make any other configuration changes.

## Step 2 — Configuring MySQL

NOTE: **Don't run the "mysql_secure_installation"** commannd first.

ERROR
```
Output
 ... Failed! Error: SET PASSWORD has no significance for user 'root'@'localhost' as the authentication method used doesn't store authentication data in the MySQL server. Please consider using ALTER USER instead if you want to change authentication parameters.

New password:
```
**First, open up the MySQL prompt:**
```
sudo mysql
```
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
After making this change, exit the MySQL prompt:

**you can run the "mysql_secure_installation" script without issue.**

To authenticate as the root MySQL user using a password, run this command:
```
mysql -u root -p
```

Then go back to using the default authentication method using this command:
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
```
This will mean that you can once again connect to MySQL as your root user using the sudo mysql command.


## — Testing MySQL

```
systemctl status mysql.service
```


https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04



