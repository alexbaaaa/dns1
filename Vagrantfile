# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/bookworm64"

  # Primera máquina con un servidor de DNS en este caso bind9
  # Esta máquina funciona como el master
  config.vm.define "master" do |master|
    master.vm.hostname = "master.deaw.test"
    master.vm.network "private_network", ip: "192.168.57.10"
    master.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get upgrade -y
      apt-get install -y bind9 dnsutils
    SHELL
  end

  # Segunda máquina que funciona como cliente
  config.vm.define "client" do |client|
    client.vm.hostname = "client.deaw.test"
    client.vm.network "private_network", ip: "192.168.57.200"
    client.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get upgrade -y
      apt-get install -y dnsutils
    SHELL
  end
end
