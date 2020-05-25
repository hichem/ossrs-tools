# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 1935, host: 1935
  config.vm.network "forwarded_port", guest: 1985, host: 1985

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update


# In order to avoid the message
# "==> default: dpkg-preconfigure: unable to re-open stdin: No such file or directory"
# use " > /dev/null 2>&1" in order to redirect stdout to /dev/null
# For more info see http://stackoverflow.com/questions/10508843/what-is-dev-null-21

    apt-get -y install build-essential > /dev/null 2>&1
    apt-get -y install git > /dev/null 2>&1
    apt-get -y install zip > /dev/null 2>&1
    apt-get -y install unzip > /dev/null 2>&1

    mkdir ossrs
    wget https://github.com/hichem/ossrs-tools/releases/download/srs_v2.0_tools/sb_hls_load -P ossrs/
    wget https://github.com/hichem/ossrs-tools/releases/download/srs_v2.0_tools/sb_http_load -P ossrs/
    wget https://github.com/hichem/ossrs-tools/releases/download/srs_v2.0_tools/sb_rtmp_load -P ossrs/
    wget https://github.com/hichem/ossrs-tools/releases/download/srs_v2.0_tools/sb_rtmp_load_fast -P ossrs/
    wget https://github.com/hichem/ossrs-tools/releases/download/srs_v2.0_tools/sb_rtmp_publish -P ossrs/
    wget https://github.com/hichem/ossrs-tools/releases/download/srs_v2.0_tools/srs -P ossrs/
    wget https://github.com/hichem/ossrs-tools/archive/srs_v2.0_tools.zip -P ossrs
    unzip -j ossrs/srs_v2.0_tools.zip -d ossrs/
    rm ossrs/srs_v2.0_tools.zip

  SHELL
end
