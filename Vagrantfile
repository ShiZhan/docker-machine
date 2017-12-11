# -*- mode: ruby -*-
# vi: set ft=ruby :

home_folder = Dir.home()
ssh_key_public  = File.readlines("./insecure-key.pub").first.strip

Vagrant.configure("2") do |config|
  config.vm.define "dm" do |dm|
    dm.vm.box = "envimation/ubuntu-xenial-docker"
    dm.vm.box_version = "1.0.0-1502068394"
    dm.vm.box_check_update = false
    dm.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
      vb.cpus = 4
    end
    dm.vm.network "private_network", ip: "192.168.33.11"
    dm.vm.hostname = "docker-machine"
    dm.vm.synced_folder "#{home_folder}", "/vagrant_data", create: true, owner: "root", group: "root"

    dm.vm.provision "shell", inline: <<-SHELL
      echo #{ssh_key_public} >> /home/vagrant/.ssh/authorized_keys
      echo "Docker machine based on ubuntu-xenial-docker vagrant box" > /etc/motd
    SHELL
  end
end
