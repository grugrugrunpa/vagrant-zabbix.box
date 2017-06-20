# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  ["master01", "node01", "node02", "node03"].each_with_index do |n,i|
  	config.vm.define n do |v|
	 v.vm.hostname = n
	 v.vm.network :private_network, ip: "192.168.33.#{50+i}"
	end
  end
  config.vm.provision "ansible" do |ansible|
   ansible.playbook = "site.yml"
   ansible.sudo = true
   ansible.verbose = 'vvv'
   ansible.host_key_checking = false
   ansible.inventory_path = "production"
#   ansible.limit = i == 0 ? "master" : "slave"
  end
end
