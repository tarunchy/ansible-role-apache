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

## Creating a Role from the Command Line

To create a role using the command line, run the following command:

```
$ansible-galaxy init ansible-role-apache

$tree ansible-role-apache
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
└── vars/
    └── main.yml

```
