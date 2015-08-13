# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 3001, host: 3001
  config.vm.network "forwarded_port", guest: 443, host: 8443
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "2048"
    vb.cpus = "2"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y python-pip python-dev
    sudo pip install ansible
    sudo mkdir /etc/ansible
    sudo echo "[local]" >> /etc/ansible/hosts
    sudo echo "localhost ansible_connection=local" >> /etc/ansible/hosts
    sudo echo "[tater]" >> /etc/ansible/hosts
    sudo echo "localhost ansible_connection=local" >> /etc/ansible/hosts
    echo "To run the ansible playbook ssh into the vm with 'vagrant ssh' and run this command:"
    echo "sudo ansible-playbook /vagrant/site.yml --ask-vault-pass"
  SHELL
end
