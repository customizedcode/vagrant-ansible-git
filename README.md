# vagrant-ansible-git
Version 1.0

MIT License

11/29/2018

This is a vagrant template for running Ansible in a 
VirtualBox VM.

It should run on MacOS X and Linux with VirtualBox, but I have not tested it.

To run:

1 - Install VirtalBox on your machine.
https://www.virtualbox.org/wiki/Downloads

1 - Install Vagrant on your machine.
https://www.vagrantup.com/downloads.html

2 - Download vagrant-ansible-git from Github
https://github.com/customizedcode/vagrant-ansible-git

3 - From command line (on Windows use Powershell with admin privledge), change to vagrant-ansible-git

4 - type:

`$ vagrant up`

It will install the VM and the dependancies you need.

This vagrant file will also install Python3, Pip and pip install Ansible.
It will also add other variables in the .bashrc script.

In the directory ,/ansible are where the playbook files are stored.
Use your favorite IDE/Editor to add or edit these files.


5 - To access the vagrant vm through command line type:

`$ vagrant ssh`

From here, you can execute commands.

`$ ansible --version`

The ansible playbooks and resources live in this directory.

/home/ansible

and can be accessed with this alias

`$ adir`

Shows the version of ansible running.

`$ ansible -m ping localhost --connection=local`

Pings the VM your using.

`ansible-playbook -K -l localhost playbooks/playbook.yml`

Run a local playbook on the VM.  When your prompted for the password, use "vagrant"

6 - To shut down vagrant vm, first exit out of the shell.

`$ exit`

Then, on the command prompt:

`$ vagrant halt`

Keep in mind, you may need to adjust network and firewall settings on your machine, to make this works.
I have placed various readme.txt to give you hints of how these files and directories can be used. 
Please read the documentation on Vagrant and Ansible for further information on how to use this tools.

