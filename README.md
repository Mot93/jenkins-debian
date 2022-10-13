# Setting up Debian/Ubuntu Jenkins server
This project help create a jenkins server on a Debian/Ubuntu server.

## Creating the VM
Use vagrant to create the VM.

    vagrant up

Remember to chage the interface for the public ip on the Vagrant file:

    config.vm.network "public_network", type: "dhcp", bridge: "enp3s0"

## Jenkins
Jenkins is, by deafult, listening on `port 8080`. 
To reach it visit the address [`http://localhost:8080/`](http://localhost:8080/).

In order to unlock Jenkins the first time is launched, get the password from the file `/var/lib/jenkins/secrets/initialAdminPassword` inside the VM.

    vagrant ssh
    cat /var/lib/jenkins/secrets/initialAdminPassword
