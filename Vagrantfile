# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  Vagrant.require_version ">= 1.4.3"

  config.ssh.forward_agent = true

  config.vm.define :hired do | hired |
    hired.vm.box = "bento/centos-7.1"

    # Create a private network
    hired.vm.network :private_network, ip: "192.168.22.55"
    hired.vm.network :forwarded_port, guest:22, host: 2230, auto_correct: true
    hired.vm.hostname = "hired.vagrant-local.com"

    #VirtualBox provider
    hired.vm.provider :virtualbox do |vb|
      vb.name = "hired"
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
    end

  end
end
