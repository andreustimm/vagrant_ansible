# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"

  $provision_install = <<-SCRIPT
    sudo apt update && \
    sudo apt install vim ansible openssh-server -y
  SCRIPT

  config.vm.define "web" do |web|
    web.vm.hostname = "web"
    web.vm.network "public_network",ip: "192.168.0.31"
    web.vm.provision "shell", inline: $provision_install
    web.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/lamp.yml"
    end
  end

  config.vm.define "banco" do |banco|
    banco.vm.hostname = "banco"
    banco.vm.network "public_network",ip: "192.168.0.51"
    banco.vm.provision "shell", inline: $provision_install
    banco.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/lamp.yml"
    end
  end
end
