# ANSIBLE REFACTORING, ASSIGNMENTS AND IMPORTS

## Introduction 

### Refactoring in Ansible
Refactoring in Ansible involves restructuring your playbooks, roles, and tasks to improve their readability, maintainability, and efficiency without changing their functionality. This can include breaking down complex playbooks into smaller, reusable components, simplifying tasks, and improving variable management.

- Common refactoring techniques in Ansible:

1. Splitting Playbooks: Breaking a large playbook into smaller, more manageable playbooks.
2. Using Roles: Organizing tasks into roles to promote reuse and modularity.
3. Variable Consolidation: Centralizing variables in a vars file or in group/host variable files.
4. Task Optimization: Combining similar tasks, removing redundant tasks, and using loops.

Example before refactoring:

```
- hosts: webservers
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start Nginx
      service:
        name: nginx
        state: started
```

### Assignment in Ansible
Assignment in Ansible refers to setting values to variables, which can be used to store data such as configuration parameters, credentials, or dynamic values that can be reused throughout playbooks and roles.

- Methods of assignment in Ansible:

1. Direct Assignment: Assigning variables directly within a playbook or task.
2. Using vars Files: Storing variables in separate files and including them in playbooks.
3. Group/Host Variables: Defining variables specific to groups of hosts or individual hosts in inventory files.

Example:
```
# Direct Assignment
- hosts: webservers
  vars:
    nginx_package: nginx
  tasks:
    - name: Install Nginx
      apt:
        name: "{{ nginx_package }}"
        state: present

# Using `vars` File
# vars/nginx.yml
nginx_package: nginx

# Playbook
- hosts: webservers
  vars_files:
    - vars/nginx.yml
  tasks:
    - name: Install Nginx
      apt:
        name: "{{ nginx_package }}"
        state: present
```

### Import in Ansible
Importing in Ansible is used to include tasks, playbooks, or roles into other playbooks, allowing for better organization and reuse of code. There are two main directives for this purpose: import_tasks, import_playbook, and import_role.

Examples:

```
# Importing Tasks
- hosts: webservers
  tasks:
    - import_tasks: tasks/nginx_install.yml

# tasks/nginx_install.yml
- name: Install Nginx
  apt:
    name: nginx
    state: present

# Importing Playbooks
# main_playbook.yml
- import_playbook: webservers.yml
- import_playbook: databases.yml

# Importing Roles
- hosts: webservers
  tasks:
    - import_role:
        name: nginx
```
