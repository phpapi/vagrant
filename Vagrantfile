# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
 
  config.vm.box = "./CentOS-7.1.1503-x86_64-netboot.box"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.synced_folder "../www/htdocs", "/opt/htdocs"

  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo /sbin/iptables -I INPUT -p tcp --dport 80 -j ACCEPT 
    sudo /usr/local/webmaster/nginx/sbin/nginx
  SHELL

end
