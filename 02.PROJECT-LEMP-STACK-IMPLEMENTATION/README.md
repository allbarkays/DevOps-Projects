# project2

# WEB STACK IMPLEMENTATION (LEMP STACK)

set up another instance in AWS

run   `sudo apt update`

installed nginx with `sudo apt install nginx`

checked the status of the nginx and it is active (running)

![installed-nginx-active-running.PNG](./images/installed-nginx-active-running.PNG)


created project2 repository in gitHub with project.md file and images folder

set the server up for inbound html traffic

Then, confirmed same from the terminal with:

`curl http://localhost:80`

also checked same from the browser in html and welcome to Nginx page

![welcome-to-nginx.PNG](./images/welcome-to-nginx.PNG)

IP: curl -s http://169.254.169.254/latest/meta-data/public-ipv4

54.172.246.121ubuntu@ip-172-31-90-217:~$





installed MySql server
`sudo apt install mysql-server`

logged into MySql and I ran the security script

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`, though I changed the password here


completed set up password for MySql and logged in succesfully

![MySql-login-password.PNG](./images/MySql-login-password.PNG)


installed PHP and php-mysql to communicate with the MySql database:
`sudo apt install php-fpm php-mysql`


![Nginx-successful.PNG](./images/Nginx-successful.PNG)


Reload nginx
`sudo systemctl reload nginx`



![Hello-LEMP.PNG](./images/Hello-LEMP.PNG)


LEMP is fully installed and operational now. Next up is to test PHP with nginx

we can see detailed info of the server after adding the php file
`sudo nano /var/www/projectLEMP/info.php`

```
<?php
phpinfo();
```


![info-php.PNG](./images/info-php.PNG)

Then, for security reasons because of the information in the php info page on server, I removed with `sudo rm /var/www/projectLEMP/info.php`

created example_user and example_database

`CREATE DATABASE `example_database`;`

`CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';` 

used a different password for this user so I had to change the password in subsequent stages needing the password

inserted four rows of content in the database table using the command:

`INSERT INTO example_database.todo_list (content) VALUES ("My first important item");` 

confirmed data in the table using:

`SELECT * FROM example_database.todo_list;` 

inserted PHP script in to query the content of todo_list table

And confirmed this changes by adding */todo_list.php* to the (URL) public IP address on the webpage

![todo_list.PNG](./images/todo_list.PNG)



PHP ready to connect and interact with the MySql server
