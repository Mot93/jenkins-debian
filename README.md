# Setting up Debian/Ubuntu Jenkins server
This project help create a jenkins server on a Debian/Ubuntu server.

## Creating the VM
The creation of the VM has been automated by [Vagrant](https://www.vagrantup.com/).

Use Vagrant to create the VM:

    vagrant up

Remember to chage the interface for the public ip on the Vagrant file:

    config.vm.network "public_network", type: "dhcp", bridge: "enp3s0"

## Provvisioning the VM
The install process behind Jenkins has been automated via the [Ansible](https://www.redhat.com/en/technologies/management/ansible).

All the Ansible automation can be found in the file `playbook.yaml`.

It's possible to run the playbook again against the vm by using the inventory Asnible created by Vagrant:

    ansible-playbook playbook.yaml -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory

## Jenkins
Jenkins is, by deafult, listening on `port 8080`. 
To reach it visit the address [`http://localhost:8080/`](http://localhost:8080/).

In order to unlock Jenkins the first time is launched, get the password from the file `/var/lib/jenkins/secrets/initialAdminPassword` inside the VM:

    vagrant ssh
    cat /var/lib/jenkins/secrets/initialAdminPassword
