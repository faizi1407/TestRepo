# encoding: utf-8
# This file originally created at http://rove.io/21ca1465297b6590e159e851d8ad022a

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "opscode-ubuntu-12.04_chef-11.4.0"
  config.vm.box_url = "https://opscode-vm-bento.s3.amazonaws.com/vagrant/opscode_ubuntu-12.04_chef-11.4.0.box"
#config.vm.network :public_network
  config.ssh.forward_agent = true


config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get update
    sudo apt-get install -y curl 
	sudo apt-get install git
	sudo apt-get install maven
curl -sL https://chef.io/chef/install.sh | sudo bash
SHELL

    


  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]
		chef.add_recipe "apt"
        chef.add_recipe "mysqltest"
chef.add_recipe "apache2"
chef.add_recipe "apache2::mod_jk"

chef.json = { :apache => { :default_site_enabled => true } }
    end
    

config.vm.provider "virtualbox" do |v|
  v.memory = 2048
  v.cpus = 1
end
  end
