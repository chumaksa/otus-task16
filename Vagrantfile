# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.cpus = 2
  end
  
  boxes = [
  	{
  		:name => "web",
  		:ip => "192.168.56.10",
  	},
  	{
  		:name => "log",
  		:ip => "192.168.56.15",  		
  	}
  ]
  
  boxes.each do |opts|
  	config.vm.define opts[:name] do |config|
  		config.vm.hostname = opts[:name]
  		config.vm.network "private_network", ip: opts[:ip]
  	end
  end
  
end
