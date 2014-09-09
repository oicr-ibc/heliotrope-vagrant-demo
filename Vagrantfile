# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise64"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Redirect networking from host to guest
  # Now you can navigate to https://localhost:8443/
  config.vm.network :forwarded_port, host: 8443, guest: 443

  # For VirtualBox, set RAM availability, and use two CPUs.
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
    v.customize ['storagectl', :id, "--name", "SATA Controller", '--hostiocache', 'off']
  end

  config.vm.provision "shell" do |shell|
    shell.path = "https://raw.githubusercontent.com/oicr-ibc/heliotrope/develop/etc/vagrant/bootstrap.sh"
    shell.privileged = false
  end

end
