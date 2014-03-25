# -*- mode: ruby -*-
# vi: set ft=ruby :

# Stripped-down Vagrantfile for development


Vagrant::Config.run do |config|

  config.vm.box = 'ubuntu'
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.ssh.forward_agent = true

  config.vm.customize [
    'modifyvm', :id,
    "--natdnshostresolver1", "on",
    "--natdnsproxy1", "on",
    "--memory", 1024
  ]

  # config.vm.provision :shell, :inline => "apt-get update -q && cd /vagrant && /bin/sh setup.sh"
end

Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.10.200"
  if File.exist?("../inbox-eas")
    puts 'Found EAS...'
    config.vm.synced_folder "../inbox-eas", "/vagrant-eas"
  end
  if File.exist?("../inbox-util")
    puts 'Found utils...'
    config.vm.synced_folder "../inbox-util", "/vagrant-util"
  end
end
