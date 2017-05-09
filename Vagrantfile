# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant configurations
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

Vagrant.configure("2") do |config|
    config.vm.box = "centos/6"

    config.vm.provider :virtualbox do |v|
        v.name = "VIB Vagrant Devel"
    end

    config.vm.synced_folder ".", "/vagrant", type: "sshfs"

    # install VIB author
    config.vm.provision "shell", inline: <<-SCRIPT
        set -e
        cd /vagrant/rpm/
        yum -y install *.rpm
    SCRIPT

    # (always) generate VIB/ZIP
    config.vm.provision "shell",  run: "always", inline: <<-SCRIPT
        set -e
        cd /vagrant/
        vibauthor -C -t vib/ -v fw-vnc.vib -O fw-vnc.zip --force
    SCRIPT
end
