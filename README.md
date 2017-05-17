# Vagrant + Ansible Test task

  1. Create Vagrantfile having 4 Linux instances
  2. Machines should be provisioned automatically via ansible/chef/shell:
  3. Two apache servers with test pages "I am server 1/2"
  4. Haproxy for balancing 2 apache servers
  5. Icinga2 web node for monitoring these all hosts

At all machines uses additional network. For Haproxy and Icinga instances uses port forwading option.
For starting clone repo:
```sh
$ git clone https://github.com/Andriycherepanov/vagrant_ansible.git
```
Jump into  direcotry vagrant_ansible
```sh
$ cd vagrant_ansible
```
Start vagrant
```sh
$ vagrant up
```
After creating and instance provisioning Test page and Icinga will be available in your browser by url's:
```sh
http://127.0.0.1:8082
```
and Icinga
```sh
http://127.0.0.1:8080
```
All needed credential will be provided in file password which was created in vagrant directory.

Best regards,
Andriy
