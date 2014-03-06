# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    # base box
    config.vm.box = "CentOS-6.3-x86_64-minimal"
    config.vm.box_url = "https://dl.dropbox.com/u/7225008/Vagrant/CentOS-6.3-x86_64-minimal.box"

    # port forward
    config.vm.network :forwarded_port, guest: 8080, host: 8080
    config.vm.network :forwarded_port, guest: 3030, host: 3030
    # network adapter
    config.vm.network :public_network
    config.vm.network :private_network, ip: "192.168.33.10"

    # VM configure
    config.vm.provider "virtualbox" do |vb|
        vb.name = "centos63-nodejs"
        vb.customize ["modifyvm", :id, "--memory", 512]
        vb.customize ["modifyvm", :id, "--cpus", 1]
    end

    # shared folder
    config.vm.synced_folder "../..", "/workspace"

    # install package & library
    config.vm.provision :shell, :path => "./package/1.library.sh"
    config.vm.provision :shell, :path => "./package/2.pythonInstall.sh"
    config.vm.provision :shell, :path => "./package/3.nodejsInstall.sh"
    config.vm.provision :shell, :path => "./package/4.protocolBufferInstall.sh"
    config.vm.provision :shell, :path => "./package/5.iptables.sh"
end
