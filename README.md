# Ansible Role: Apache

This repository explains how to develop an Ansible role for Apache.

## What are Ansible Roles?

- Puppet -> Modules
- Chef -> Cookbooks
- Ansible -> Roles

Ansible roles are a collection of tasks, templates, and configurations needed to set up a specific application or service. In this case, we're working with an Apache role, which includes everything required to run Apache.

## Components of an Apache Role:

1. **defaults**: Contains default variables for the role or application.
2. **files**: Stores static files that will be copied to remote machines.
3. **handlers**: Contains tasks triggered by specific actions (e.g., restarting the Apache service when the `httpd.conf` file changes).
4. **meta**: Provides information about the role, such as the author, supported platforms, dependencies (if any), etc.
5. **tasks**: Implements the core logic or code, such as installing packages and copying files.
6. **templates**: Stores files similar to those in the `files` directory, but with support for dynamic content using the Jinja2 template language (`.j2` files).
7. **vars**: Holds variables similar to those in the `defaults` directory, but with higher priority.
8. **tests**: Contains test cases to validate the functionality of the role. Test cases can be written using Ansible playbooks and executed with the ansible-playbook command.

## Creating a Role from the Command Line

To create a role using the command line, run the following command:

```
$ansible-galaxy init ansible-role-apache

$tree ansible-role-apache
ansible-role-apache/
ansible-role-apache/
├── README.md
├── defaults/
│   └── main.yml
├── files/
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   └── main.yml
├── templates/
├── tests/
│   ├── inventory
│   └── test.yml
└── vars/
    └── main.yml


```

# Using the tests Folder

The tests folder is used to store test cases for your role. Typically, you would create an Ansible playbook named test.yml and an inventory file within this folder.

To execute the test playbook, run the following command from the root of your role directory:

```
ansible-playbook -i tests/inventory tests/test.yml --extra-vars "ansible_sudo_pass=your_password"

```

Replace your_password with the sudo password for the remote machine(s) in the inventory file. You can also use an Ansible Vault-encrypted password file or other authentication methods based on your setup.

The test.yml playbook should include the role you want to test, and you can include any required variables, tasks, or additional roles needed for testing.

For example, your test.yml file may look like this:

```
---
- hosts: all
  roles:
    - ansible-role-apache
  tasks:
    # Add any additional tasks required for testing


```

Don't forget to update your inventory file in the tests folder with the appropriate remote machine(s) information.

