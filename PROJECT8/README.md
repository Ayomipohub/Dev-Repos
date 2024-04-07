# **Automating Loadbalancer Configuration With Shell scripting**

## `Introduction`

### Automate the Deployment of Webservers

In this course i will be automating the entire process of my previous project. I will do that by writing a shell script that when ran, all that i did manually in previous project to be done automatically.

As a DevOps Engineers automation is at the heart of the work we do. Automation helps us speed the development of services and reduce the chance of making errors in our day activity.

### What is automation?

Automation refers to the practice of using automated tools, processes, and workflows to streamline and accelerate the development, deployment, and operations of software applications. Automation plays a central role in DevOps practices, enabling teams to achieve faster delivery cycles, higher quality, and greater efficiency throughout the software development lifecycle.


#### Importance of Automation

1.  ***Speed and Efficiency***: Automation eliminates manual intervention in the CI/CD process, enabling rapid execution of tasks such as building, testing, and deploying software changes. Automated processes can run concurrently, in parallel, or sequentially, allowing teams to achieve faster delivery cycles and shorter time-to-market for new features and updates.

2.  ***Consistency and Reliability***: Automated CI/CD pipelines ensure that software changes are built, tested, and deployed consistently and reliably across different environments. Automation eliminates human errors and inconsistencies in the deployment process, leading to more predictable and stable releases.

3.  ***Scalability***: Automation enables CI/CD pipelines to scale up or down to handle varying workloads, changes in demand, or increases in development activity. Automated processes can be easily replicated, configured, and orchestrated to accommodate changes in project size, team size, or deployment complexity.

4.  ***Quality Assurance***: Automation facilitates the execution of comprehensive and repeatable tests as part of the CI/CD pipeline, including unit tests, integration tests, functional tests, performance tests, and security tests. Automated testing helps identify defects, regressions, and quality issues early in the development process, ensuring that software changes meet quality standards before deployment.


## **Deploying And Configuring Webservers and Load Balancer**

Step 1: Launch 3 EC2 Instances
We will provision 3 EC2 instance, two will of these will be our webserver and one will be a load balaner

i. Launch 2 EC2 instances and name each "WS_1" and "WS_2" (Webservers)

ii. Launch another EC2 instance and name it "load balancer"

Step 2: Open New Security Group For Both Webservers and load balancer
i. For the webservers and load balancer, go to the security groups

ii Edit inbound rules on open port 8000 for our both WS_1 and WS_2 and port 80 for our load balancer

iii. Allow traffic from anywhere on the open ports

iv. ssh into the three instances

Step 3: Automating Webservers Configurartion With Shell Script

i. Paste the shell script below in a file on webserver 1 and 2 instances to configure each webservers

    #!/bin/bash

    ####################################################################################################################
    ##### This automates the installation and configuring of apache webserver to listen on port 8000
    ##### Usage: Call the script and pass in the Public_IP of your EC2 instance as the first argument as shown below:
    ######## ./install_configure_apache.sh 127.0.0.1
    ####################################################################################################################

    set -x # debug mode
    set -e # exit the script if there is an error
    set -o pipefail # exit the script when there is a pipe failure

    PUBLIC_IP=$1   # place the public ip address of each webserver

    [ -z "${PUBLIC_IP}" ] && echo "Please pass the public IP of your EC2 instance as an argument to the script" && exit 1

    sudo apt update -y &&  sudo apt install apache2 -y

    sudo systemctl status apache2

    if [[ $? -eq 0 ]]; then
     sudo chmod 777 /etc/apache2/ports.conf
     echo "Listen 8000" >> /etc/apache2/ports.conf
     sudo chmod 777 -R /etc/apache2/

     sudo sed -i 's/<VirtualHost \*:80>/<VirtualHost *:8000>/' /etc/apache2/sites-available/000-default.conf

    fi
    sudo chmod 777 -R /var/www/
    echo "<!DOCTYPE html>
       <html>
       <head>
           <title>My EC2 Instance</title>
       </head>
       <body>
           <h1>Welcome to my EC2 instance</h1>
           <p>Public IP: "${PUBLIC_IP}"</p>
       </body>
       </html>" > /var/www/html/index.html

    sudo systemctl restart apache2

![alt text](<images/LB-SHELL SCRIPT.PNG>)

