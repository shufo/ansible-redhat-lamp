# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :develop do |machine|
    
    machine.vm.hostname = "web"
    machine.vm.box = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
    
    machine.vm.network :private_network, ip: "192.168.33.10", auto_machine: false
    
    machine.vm.synced_folder ".", "/vagrant"
    
    machine.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", 4096, "--cpus", 4]
      v.gui = false
    end
    
    # load bridge module
    machine.vm.provision "shell", inline: "modprobe bridge"
    
    # main provisioning
    machine.vm.provision "ansible" do |ansible|
        ansible.sudo = true
        ansible.verbose = 'vv'
        ansible.playbook = "provisioning/site.yaml"
        ansible.inventory_path = "provisioning/ansible_hosts"
        ansible.limit = "all"
    end
    
    # local hosts file setting. if u don't want to change hosts file, comment out below.
    machine.vm.provision "ansible" do |ansible|
        ansible.sudo = true
        ansible.ask_sudo_pass = true
        ansible.verbose = 'vv'
        ansible.playbook = "provisioning/localhost.yaml"
        ansible.inventory_path = "provisioning/ansible_hosts"
        ansible.limit = "all"
    end
  end
end
