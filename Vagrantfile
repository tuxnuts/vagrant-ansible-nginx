# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.define "nginx" do |nginx|
        # Select Virtualbox template for Ubuntu 16.04 (Xenial).
        nginx.vm.box = "puppetlabs/ubuntu-16.04-32-nocm"
        
        # Configure private network IP and hostname.
        # nginx.vm.network :public_network, type: "dhcp"
        nginx.vm.network :private_network, ip: "192.168.7.7"
        nginx.vm.hostname  = "webserver.local"

        # Explicitly forward any ephemeral ports required.
        nginx.vm.network "forwarded_port", guest:8000, host:8000

        # Sync vagrant directory on Linux platforms.
        nginx.vm.synced_folder ".", "/vagrant"
        # Sync vagrant directory via NFS on other platforms
        # nginx.vm.synced_folder ".", "/vagrant", type: "nfs"

        # Configure Virtualbox settings for vm name and memory allocation.
        nginx.vm.provider "virtualbox" do |vb|
            vb.customize ["modifyvm", :id, "--name", "webserver.local"]        
            vb.memory = 1024
        end
    
        # Handover to Ansible to perform provisioning tasks.
        nginx.vm.provision :ansible do |ansible|
            ansible.playbook = "provisioning/playbook.yml"
        end
    end
end
