# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  ##### VMs definitions #####

  config.vm.define "node1" do |machine|
    machine.vm.network "private_network", ip: "192.168.56.101", virtualbox__intnet: "vagrant_network"
  end

  config.vm.define "node2" do |machine|
    machine.vm.network "private_network", ip: "192.168.56.102", virtualbox__intnet: "vagrant_network"
  end

  config.vm.box_check_update = false
  config.vm.provision :ansible do |ansible|
    ansible.limit = "all"
    ansible.playbook = "./provision/provision.yaml"
  end
  config.vm.provider :libvirt do |v|
    v.memory = 1024
    v.cpus = 1
  end
end