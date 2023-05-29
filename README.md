# Deprecated 
# This repo is archived and hasnt been maintained or tested in quite some time. 
# consider finding another solution like Ansible molecule 


ANSIBLE-DOCKER-PLAYGROUND
=========

 Provision docker containers using inventory for testing ansible roles

 An inventory file "local" is added for development purposes
------------
This playbook spins up a centos7 container that has the following
user: ansible
password: ansible
packages:
  - Development Tools
  - firewalld
  - gcc & glibc
  - openssh
  - cmake



Role Variables

 docker_inventory variable names and docker_inventory_group
 must match names in local inventory file as well.

 inventory:
 - name: dolly_one
 - name: dolly_two
 - name: dolly_three
 - name: dolly_four
 - name: dolly_five
 docker_inventory: "{{inventory}}"
 docker_inventory_group: [ 'dolly_one', 'dolly_two', 'dolly_three', 'dolly_four', 'dolly_five', ]
 docker_groups: [ 'net-docks', ]
 docker_privileged: true
 docker_network: null
 docker_ip: "127.0.0.1"
 docker_ssh_user: "ansible"
 docker_ssh_pass: "docker"
 docker_use_tls: true
 docker_state: "started"
 docker_use_docker_connection: true


DEPENDENCIES

REQUIREMENTS
--Docker   
--Ansible


Test Playbook

To run the playbook and spin up 5 docker containers
run the following command

ansible-playbook -i inventory/local roles/ansible-docker-playground/playbook.yml

REMINDER
Docker should be running a process in the foreground in your container and will be spawned as PID 1 within the container's pid namespace.
Docker is designed for process isolation, not for OS virtualization, so there are no OS processes and daemons running inside the container (like systemd, cron, syslog, etc), only your entrypoint or command you run.

License
---
BSD

Author Information
 Twitter: @TechGameTeddy

 Inspired by: Chris Meyers
 https://www.ansible.com/blog/testing-ansible-roles-with-docker
