# otus-task16

# Настраиваем центральный сервер для сбора логов

Настроить стенд Vagrant с двумя виртуальными машинами: backup_server и client.

### Подготовка.

Для выполнения задания будем использовать виртуальные машины развёрнутые с помощью vagrant. \
Vagrantfile имеет следующий вид:
```

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provider :virtualbox do |v|
    v.memory = 1512
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
```

Для предварительной подготовки машин будем использовать Ansible. \
Все необхдимые файлы есть в репозитории. \
После равёртования и предварительной настройки тестового стенда перейдём непосредственно к выполнению задания.

### Решение.

