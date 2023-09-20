# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.vm.define "web" do |web|
    web.vm.hostname = "web"
    web.vm.network "public_network",ip: "192.168.50.31"

    web.vm.provider :virtualbox do |vb|
      vb.memory = 1024
      vb.cpus = 2
    end

    web.vm.provision "shell", path: "scripts/setup.sh"
    web.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
    end
  end

  config.vm.define "banco" do |banco|
    banco.vm.hostname = "banco"
    banco.vm.network "public_network",ip: "192.168.50.51"

    banco.vm.provider :virtualbox do |vb|
      vb.memory = 1024
      vb.cpus = 2
    end

    banco.vm.provision "shell", path: "scripts/setup.sh"
    banco.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
    end
  end
end
