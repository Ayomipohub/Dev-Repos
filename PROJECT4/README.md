# **WEB STACK IMPLEMENTATION (LAMP STACK)**

> A web stack, also known as a technology stack or solution stack, refers to the collection of software and technologies used to develop and run web applications. It encompasses everything from the server infrastructure to the front-end user interface.

> A web stack is a collection of similar things or object (softwares) which work together in an interconnected way to run a function. There are different types of web stack and they all perform different function. There are different types of web stacks which are;

1. LAMP (Linux, Apache, MySQL, PHP or Python, or Perl)
2. LEMP (Linux, Nginx, MySQL, PHP or Python, or Perl)
3. MERN (MongoDB, ExpressJS, ReactJS, NodeJS)
4. MEAN (MongoDB, ExpressJS, AngularJS, NodeJS)
These stacks all have diferent function. In this project, we will be focusing on LAMP Stack

## What is LAMP STACK?

The LAMP stack is a popular open-source web development stack that consists of four main components: Linux, Apache, MySQL, and PHP/Perl/Python. Each component plays a specific role in supporting the development and hosting of dynamic web applications.

## Prerequisite

1.  Open AWS account. [CLICK HERE](https://portal.aws.amazon.com/billing/signup#/start/email) to create one.
    
2.  Good knowledge of Linux
    
3.  Understand ssh kegs. click on this link to learn more on [SSH](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-20-04)



## **GETTING STATED WITH LAMP STACK**

1. **Launch an Ubuntu Instance on AWS Console and SSH Into From Your Terminal**

![Alt text](<images/ssh apache.PNG>)

### *ssh into your ubuntu Ec2 instance*
    
    ssh -i path/to/.pem ubuntu@public_ip_address
    

2. **Installating Apache**

### update package lists and apt repositories

    sudo apt update
    
### Install apache web server
    sudo apt install apache2
    
### Allow firewall for apache
    sudo ufw allow in "Apache"

> NOTE: The step above will allow firewall for apache once it is enabled, it is important we allow firewall for ssh. ssh runs on port 22, if firewall is not allowed for ssh running on port 22, connection to the ubuntu instance via ssh will be permanently denied

    sudo ufw allow 22

### *Confirm Apache web server is sucessfully installed*

    sudo systemctl status apache2

![Alt text](<images/apache running.PNG>)

To access your web server on your browser

    http://ubuntu_instance_public_ip_address

![Alt text](<images/apache page.PNG>)


3. **Installating Mysql**

mysql will be installed as a database to store data for our web application.

    sudo apt install mysql-server

### login into mysql consol

 Log into mysql console as the root user

        sudo mysql

![Alt text](<images/sudo mysql.PNG>)


### Setting up root password for root user using mysql native password

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

> Exit Mysql shell

`   Exit`

### Secure mysql installation

sudo mysql_secure_installation

> This will ask if you want to configure the VALIDATE PASSWORD PLUGIN, After the validation is completed, login to MYSQL and input the password by adding the -p flag.

        sudo mysql -p


After succcessful password validation and confimation of login, you can exit MYSQL

`   Exit`

4. **Installing php**

### We will install 3 packages namely php, libapache2-mod-php, php-mysql. run this command to install all packages listed.

    sudo apt install php libapache2-mod-php php-mysql

### Confirm the php version

    php -v

  ![Alt text](<images/php version.PNG>) 



At this point we have successfully installed all 4 applications that make up the lamp stack

- [x] Linux
- [x] Apache Http Server
- [x] MySQL
- [x] PHP


5. **Configuring Apache Web Server To Serve As A Virtual Host**

> We need to create a directory for our codes to be hosted at the location "/var/www/html/projectlamp", "project lamp" can be named any name. The directory will contain the php codes which apache will serve. The codes are not limited to php codes but also html, css, javascript e.t.c. . Apache web server is smart enough to know this location and serve it with the help of its configuration file.

### Create the directory for projectlamp using ‘mkdir’ command

    sudo mkdir /var/www/projectlamp

> Next, assign ownership of the directory with your current system user:

    sudo chown -R $USER:$USER /var/www/projectlamp

### Create and open a new configuration file in Apache’s sites-available directory.

    sudo vi /etc/apache2/sites-available/projectlamp.conf

<VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

### list (ls()) the new file in the sites-available directory.

    sudo ls /etc/apache2/sites-available

> The output of the above command should be similar to this below

    000-default.conf  default-ssl.conf  projectlamp.conf


Thus, we have set /var/www/projectlampl as the root directory for Projectlamp.

### Let us enable the new virtual host with the a2ensite command

    sudo a2ensite projectlamp

### Let us enable the new virtual host with the a2ensite command

sudo a2ensite projectlamp


### Run the below command to check for syntax errors in the configuration file.

    sudo apache2ctl configtest

Reload Apache service for changes to take efffect

sudo systemctl reload apache2

![Alt text](<images/apache reload.PNG>)


### Create an index file in the projectlamp folder.

![Alt text](<images/echo apache.PNG>)


### Go to your browser and try to open your website URL using IP address:

    http://<Public-IP-Address>:80

> Prefarrably you can also use the DNS name, the port is optional as it defaults to 80.

    http://<Public-DNS-Name>:80

![Alt text](<images/apache page.PNG>)


6. **Enable PHP on the Website**

> With the default DirectoryIndex settings on Apache, the index.html file takes precedence, lets modify this and give precedence to the index.php file.

> We need to edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive:

    sudo vim /etc/apache2/mods-enabled/dir.conf

<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>

> Save and close the file, The Apache service needs to be restarted for the changes to take effect.

    sudo systemctl reload apache2

### Create a new file named index.php inside the projectlamp root folder:

    vim /var/www/projectlamp/index.php
```
<?php
 phpinfo();
```  
    
> Refresh the webpage to get a display similar to the below screenshot.

![Alt text](<images/apache php.PNG>)


> It is advisable to remove the file as it contains sensitive information about your server and php site config.

    sudo rm /var/www/projectlamp/index.php

