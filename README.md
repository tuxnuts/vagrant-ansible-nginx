# vagrant-ansible-nginx

nginix web server – auto provisioned with Ansible &amp; Vagrant

This automation solution for provisioning and configuring an ngnix web server relies on Vagrant for virtual machine management, Virtualbox hypervisor and Ansible for provisioning. Install the following software on your provisioning host...

  Virtualbox (v5.2 recommended) https://www.virtualbox.org/wiki/Downloads
  
  Vagrant v2.1.4 (recommended)  https://www.vagrantup.com/downloads.html
  
  Ansible (v2.6 recommended)    https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html


Installing the Vagrant “hostsupdater” plugin is recommended so the web server may be resolved by host name as well as IP address...

	vagrant plugin install vagrant-hostsupdater

The plugin allows the freshly provisioned guest host to be added into your local hosts file during provisioning. Alternatively, manually add this host entry into your local hosts file or DNS...

	192.168.7.7  webserver.local

Modify the IP address in Vagrantfile if it will cause conflict in your network.

The automation is initiated by running…

	 sudo vagrant up

Upon completion browse to either…

http://webserver.local:8000  or  http://192.168.7.7:8000

#### Assumptions:

Developed and tested on Ubuntu 18.04 LTS (Bionic) 64-bit provisioning host. Has not been tested on other platforms. 

No DHCP used. Provisioned guest host IP address and host name hard coded in Vagrantfile.

No SELinux is enabled or other security changes required.

No firewall changes required for both the provisioning host and guest host to access Ubuntu repositories and other required Internet resources...

https://app.vagrantup.com/puppetlabs/boxes/ubuntu-16.04-32-nocm

https://github.com/puppetlabs/exercise-webpage
