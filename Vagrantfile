# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  ##### VMs definitions #####
  config.vm.define "server1" do |server1|
     server1.vm.hostname = "server1"
     server1.vm.network "private_network", ip: "192.168.56.11"

     config.vm.provider "virtualbox" do |vb|
       vb.memory = 2048
       vb.cpus = 2
     end
  end

  config.vm.define "server2" do |server2|
     server2.vm.hostname = "server2"
     server2.vm.network "private_network", ip: "192.168.56.12"

     config.vm.provider "virtualbox" do |vb|
       vb.memory = 2048
       vb.cpus = 2
     end
  end

  config.vm.provision "ansible_local" do |ansible|
     ansible.playbook = "provisioning/playbook.yml"
     ansible.groups = {
       "challenge" => ["server[1:2]"]
     }
     ansible.compatibility_mode = "2.0"
   end
end