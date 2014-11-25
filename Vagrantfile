# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "master" do |master|
    master.vm.provision "shell", inline: "echo INSTALL MASTER"
    master.vm.box = "ubnt-server"
    master.vm.hostname = "master"
    master.vm.network "private_network", type: "dhcp"

    master.vm.provision 'ansible' do |ansible|
      ansible.playbook = "jenkins-master.yml"
      ansible.inventory_path = "hosts"
      ansible.limit = "all"
    end
  end


  config.vm.define "slave" do |slave|
    slave.vm.provision "shell", inline: "echo INSTALL SLAVE"  
    slave.vm.box = "ubnt-server"
    slave.vm.hostname = "slave-one"
    slave.vm.network "private_network", type: "dhcp"

    slave.vm.provision 'ansible' do |ansible|
      ansible.playbook = "jenkins-slave.yml"
      ansible.inventory_path = "hosts"
      ansible.limit = "all"
    end
  end 

end
