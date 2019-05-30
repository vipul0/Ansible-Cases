# Ansible-Cases
Installing Docker through Ansible

Before running the playbook, there are some assumptions we are assuming that you have already setup like,
1. Ansible Installed in your system/server,
2. already copy ssh public key from server to all slave nodes,
3. setup hosts in /etc/ansible/hosts inventory file,
4. you have tested the connection/SSH key by running following command, #ansible -m ping all


keep a point in mind we have define a host in main.yml i.e. playbook, in hosts section. if you want to run it for some different host, kindly change the host in main.yml file. if you want to run it against multiple host or group of host then first add the host in /etc/ansible/hosts inventory file. and create a new entry like this,

[DockerServer]
host1_IP
host3_IP
host3_IP
host4_IP

I have used four tasks,

1)- name: “Installing Docker Prerequisite packages”
To install the pre-requisite packages using ‘YUM’ module

2)- name: “Configuring docker-ce repo”
To download ‘docker-ce.repo’ file to ‘/etc/yum.repos.d’ directory using ‘get_url’ module

3)- name: ” Installing Docker latest version”
To install docker using ‘YUM’ module

4)- name: ” Starting and Enabling Docker service”
To start and enable the docker service using ‘service’ module


Verify Playbook syntax through CLI
# ansible-playbook main.yml --syntax-check


Run the playbook
# ansible-playbook main.yml
