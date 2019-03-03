# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
config.vm.box = "ubuntu/trusty64"
config.vm.network "private_network", ip: "192.168.33.10"
config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "setup.yml"
    ansible.host_key_checking = "false"
    ansible.limit = "all"
  end
config.vm.provider "virtualbox" do |vb|
vb.customize ["modifyvm", :id, "--memory", "1500"]
  end
end
