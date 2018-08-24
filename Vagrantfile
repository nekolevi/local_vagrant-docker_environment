def install_plugin(plugin)
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

install_plugin('vagrant-docker-compose')

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  
  config.vm.hostname = "dev.local"
  config.vbguest.auto_update = false
  
  config.vm.network "forwarded_port", id: "ssh", guest: 22, host: 2277
  config.vm.network "forwarded_port", id: "app", guest: 80, host: 8080
  config.vm.network "private_network", ip: "192.168.33.177"

  config.vm.provision "docker"
  config.vm.provision "docker_compose"
  
end
