# -*- mode: ruby -*-
# vi: set ft=ruby :

# Use vagrant up to setup the box.
# vagrant ssh if you need to edit anything on the server
# vagrant destroy to start over from scratch
# As i standard with vagrant machines, the
# vagrant user has passwordless sudo access on the guest machine

# Put a copy of the crits repositories in the vagrant-folder,
# install apt-cacher-ng, and edit the crits.sh where it 
# is marked #DEVELOPMENT CHOICE# if you want to drop downloading 
# stuff again and again while testing the vagrant setup

# sudo apt-get install apt-cacher-ng
# git clone https://github.com/crits/crits.git
# git clone https://github.com/crits/crits_services.git
# git clone https://github.com/crits/crits_dependencies.git

# The crits admin username is vagrant

# The password for the self-signed sertificate/private key
# and password for the crits admin user will be put in
# /home/vagrant/CRITS_PASSWORD

# When the box is up, crits should be avalible at
# https://localhost:8443/crits

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.provision "shell", path: 'crits.sh'

  config.vm.network "public_network", bridge: 'eth1'

  config.vm.network "forwarded_port", guest: 443, host: 8443

  config.vm.provider :virtualbox do |vb|
    #vb.gui = true
    vb.customize ["modifyvm", :id, "--memory", "4096"]
  end

end
