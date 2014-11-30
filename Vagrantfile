# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 8153, host: 8153
  config.vm.network "forwarded_port", guest: 8154, host: 8154
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
	vb.customize ["modifyvm", :id, "--cpus", "4"]
  end
  config.vm.provision "shell", inline: "apt-get update && apt-get upgrade -y && apt-get install -y git && apt-get install -y dos2unix"  
  config.vm.provision "shell", inline: "curl -sSL https://get.docker.io/ubuntu/ | sh"
  config.vm.provision "shell", inline: "curl -L https://github.com/docker/fig/releases/download/0.5.2/linux > /usr/local/bin/fig"
  config.vm.provision "shell", inline: "chmod +x /usr/local/bin/fig"
  config.vm.provision "shell", inline: "cd /vagrant && fig up -d"  
end
