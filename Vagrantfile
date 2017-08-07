# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "dm" do |dm|
    dm.vm.box = "envimation/ubuntu-xenial-docker"
    dm.vm.box_version = "1.0.0-1501809231"
    dm.vm.box_check_update = false
    dm.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    dm.vm.network "private_network", ip: "192.168.33.11"
    dm.vm.hostname = "docker-machine"
    dm.vm.synced_folder "./data", "/vagrant_data",
      create: true, owner: "root", group: "root"
    dm.vm.provision "shell", inline: <<-SHELL
      echo "Docker machine based on ubuntu-xenial-docker vagrant box" > /etc/motd
    SHELL
  end
end
