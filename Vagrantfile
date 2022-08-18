# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|


  config.vm.define "apacheWebServer", autostart: true do |apacheWebServer|
    apacheWebServer.vm.box = "ubuntu/trusty64"
    apacheWebServer.vm.provision "shell", path: "apacheprovision.sh"
    apacheWebServer.vm.network "private_network", ip: "192.168.28.30"
    apacheWebServer.vm.network "forwarded_port", guest: 80, host: 8080


  end
  config.vm.define "proxyInvertido" , autostart: true do |proxyInvertido|
    proxyInvertido.vm.box = "ubuntu/trusty64"
    proxyInvertido.vm.provision "shell", path: "nginx.sh"
    proxyInvertido.vm.network "private_network", ip: "192.168.28.31"
    apacheWebServer.vm.network "forwarded_port", guest: 90, host: 9090
  end
  config.vm.define "dockerCompose", autostart: true do |dockerCompose|
    dockerCompose.vm.box = "ubuntu/trusty64"
    dockerCompose.vm.provision "shell", path: "dockerComposeProvision.sh"
    dockerCompose.vm.network "private_network", ip: "192.168.28.32"
    apacheWebServer.vm.network "forwarded_port", guest: 60, host: 6060

  end

end
