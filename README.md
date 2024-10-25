# Ansible Practical Task

This task is about deploying a spring application named PetClinic using Ansible and some of its features

## Introduction

To run this projects some considerations needs to be acknowledged first:
* This project needs an Ansible control server and a host server/managed node, both Linux.
* Ansible needs to be installed only in the control node but Python is needed on both machines.
* Both nodes needs to have a user and password, On the node as this is how the user will run some of the tasks as sudo
* Application dependencies are managed by the configuration files

### Ansible playbooks

This project is intended to run only two Ansible playbooks.
* The add-sudoers.yml file which will add the managed node user to the sudoers file. This is not recommended but for the purposes of this project, and to avoid run the subsequents ansible commands on the node providing a become password, this was done.
* The main.yml file which contains the hosts the task will run on and the role to be used.

### Configuration files

This project have only two configuration files which are hosts and ansible.cfg
* The hosts file sets the inventory for this project
* The ansible.cfg sets the configurations, applicable to this project only

### Running the playbooks

* The first Ansible playbook needed to run is the add-sudoers.yml. As this is the first time and the user will need sudo permissions, the command needs the -K flag which is short for --ask-become password. Otherwise it couldnt be possible to modify the file
```
ansible-playbook add-sudoers.yml -K
```
* The second and last one is the main.yml file. If the previous was succesful, this time no -K flag is needed.
```
ansible-playbook main.yml
```

## Accessing the application

The Petclinic application should now be running on the node. Java based applications typically run at 8080 port, so accessing this way on any browser will do:
```
<MANAGED_NODE_PUBLIC_IP>:8080
```
Replace the placeholder with the node's IP address, and application should display.
