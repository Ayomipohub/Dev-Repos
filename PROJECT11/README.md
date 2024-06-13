# ANSIBLE AUTOMATE PROJECT

## Introduction To Ansible

Ansible is an open-source automation tool used for configuration management, application deployment, and task automation. Developed by Red Hat, it aims to simplify complex tasks and make them repeatable and manageable. Here are the key points to understand Ansible:

### Key Features of Ansible:

1. Agentless: Ansible does not require any agent software to be installed on the target machines. It communicates over SSH or Windows Remote Management (WinRM).

2. Simple and Human-readable: Ansible uses YAML (Yet Another Markup Language) for its configuration files, known as playbooks, making them easy to read and write.

3. Idempotent: Ansible ensures that operations are performed only if the system state changes are necessary, preventing redundant actions.

4. Extensible: Ansible can be extended with custom modules, plugins, and inventory sources to fit specific needs.

### Components of Ansible:

1. Modules: Reusable, standalone scripts that perform specific tasks (e.g., managing packages, users, or services).

2. Playbooks: YAML files that define a series of tasks to be executed on remote systems. Playbooks are the heart of Ansible's configuration management.

3. Inventory: A list of hosts (nodes) to be managed, which can be static or dynamically generated.

4. Roles: A way to organize playbooks and tasks into reusable units, making complex playbooks easier to manage.

### Basic Workflow:

1. Define Inventory: Create an inventory file listing the servers and their groups.

2. Write Playbooks: Write YAML-based playbooks describing the desired state and tasks to be performed.

3. Execute Playbooks: Use the ansible-playbook command to apply the playbook to the target inventory.


## Ansible Client as a Jump Server (Bastion Host)

A Jump Server (sometimes also referred as Bastion Host) is an intermediary server through which access to internal network can be provided. If you think about the current architecture you are working on, ideally, the webservers would be inside a secured network which cannot be reached directly from the Internet. That means, even DevOps engineers cannot SSH into the Web servers directly and can only access it through a Jump Server – it provide better security and reduces attack surface.

On the diagram below the Virtual Private Network (VPC) is divided into two subnets – Public subnet has public IP addresses and Private subnet is only reachable by private IP addresses

![alt text](images/vpc.PNG)


### General importance:

1. Configuration Management: Ensuring that servers are configured correctly with desired settings and software.

2. Application Deployment: Automating the deployment of applications across multiple servers.
3. Task Automation: Automating repetitive administrative tasks, such as backups or user management.
4. Continuous Delivery and Integration: Integrating with CI/CD pipelines to automate the build, test, and deployment processes.


## Implementing Ansible For Automation

Step 1: Install and Configure Ansible on EC2 Instance
- Launch an instace and name it Jenkins-Ansible. We will install and configure jenkins and ansible on this instance.

- Create a new repository call ansible-config-mgt. This repository will be connected to jenkins pipeline and also store ansible files

- Install Ansible

```  
sudo apt update
sudo apt install ansible
```

*Confirm Ansible has been successfully installed*

ansible --version

![alt text](images/ansible-vers.PNG)

step 2: Configure Jenkins Build Job To Archive Your Repository Content Every Time It Is Changed
Jenkin is a pipeline for continuous integration. To create a build job, we need to have jenkins installed and configured first.

- On the same EC2 instance ansible was installed, we need to install jenkins *** Update package repositories

sudo apt update


- Install JDK

sudo apt install default-jdk-headless

- Install Jenkins

```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
/etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt-get install jenkins
```

Check if jenkins has been installed, and it is up and running

sudo systemctl status jenkins

![alt text](<images/jenkins running.PNG>)


- On our Jenkins-Ansible instance, create new inbound rules for port 8080 in security group

![alt text](<images/jenkins port.PNG>)

