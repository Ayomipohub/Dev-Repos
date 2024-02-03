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

