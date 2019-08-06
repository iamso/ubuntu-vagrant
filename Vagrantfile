# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX_NAME = ENV["BOX_NAME"] || "bionic"
BOX_URI = ENV["BOX_URI"] || "https://cloud-images.ubuntu.com/bionic/current/bionic-server-cloudimg-amd64-vagrant.box"
BOX_MEMORY = ENV["BOX_MEMORY"] || "2048"
BOX_CPU = ENV["BOX_CPU"] || "2"
BOX_DOMAIN = ENV["BOX_DOMAIN"] || "test.me"
BOX_IP = ENV["BOX_IP"] || "10.0.0.10"

Vagrant::configure("2") do |config|
  config.vm.box = BOX_NAME
  config.vm.box_url = BOX_URI
  config.vm.synced_folder File.dirname(__FILE__), "/root/shared"
  config.vm.network :forwarded_port, guest: 22, host: 10022
  config.vm.network :forwarded_port, guest: 80, host: 10080
  config.vm.network :forwarded_port, guest: 443, host: 10443
  config.vm.network :forwarded_port, guest: 9418, host: 19418
  config.vm.hostname = "#{BOX_DOMAIN}"
  config.vm.network :private_network, ip: BOX_IP

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--ostype", "Ubuntu_64"]
    vb.customize ["modifyvm", :id, "--memory", BOX_MEMORY]
    vb.customize ["modifyvm", :id, "--cpus", BOX_CPU]
  end

  config.vm.provision :shell, :inline => "SSH_KEY=your@email.tld bash <(curl -sk https://raw.githubusercontent.com/iamso/ubuntu-kickstart/master/kickstart-vagrant-18.04.sh)"
end
