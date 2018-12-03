# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<-SCRIPT
echo '****provisioning python3****'
sudo apt-get install python3 -y
echo '****provisioning python2****'
sudo apt-get install python -y
echo '****provisioning python3-pip****'
sudo apt-get install python3-pip -y
echo '****provisioning Ansible****'
sudo pip3 install ansible
echo '****done provisoning****'
echo '****modify .bashrc****'
echo "## Modify for Ansible "
echo "alias adir='cd /home/ansible'" >> /home/vagrant/.bashrc
echo "adir" >> /home/vagrant/.bashrc
exit
SCRIPT
# This is a Vagrant File for setting up Ansible
#VAGRANTFILE_API_VERSION = "2"
Vagrant.require_version ">= 1.3.5"
require 'yaml'
require 'fileutils'
Vagrant.configure(2) do |config|
	config.vm.box = "ubuntu/bionic64"
##	config.ssh.port = 4422
	config.vm.boot_timeout = 900
	config.ssh.forward_agent = true
	config.ssh.shell = "bash -c  'BASH_ENV=/etc/profile exec bash'"
##  Set ip address to not conflict with your internal network
	config.vm.network :private_network, ip: "192.168.8.7"
	config.vm.network "public_network"
	config.vm.synced_folder ".","/vagrant",type: "virtualbox", fsnotify: true
	config.vm.hostname = "Ansible-Box-Git"
	config.vm.provider :virtualbox do |vb|
		vb.name = "Ansible-Box-Git"
		vb.memory = 2048
		vb.cpus = 1
# 	These are the local files that can be edited by your favoite file editor.
	config.vm.synced_folder "./ansible", "/home/ansible", :mount_options => ["dmode=755", "fmode=755"]
#	Provisioning scripts are executed here
#   This is where we install Ansible into the VM only once.
	config.vm.provision "shell", inline: $script, run: "once"
	end
end
