Vagrant.configure("2") do |config|

  config.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
  config.vm.provision "shell", inline: <<-SHELL
    cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL

  config.vm.define "nginx" do |nginx|
    nginx.vm.box = "ubuntu/focal64"
    nginx.vm.hostname = "nginx"
    nginx.vm.network "private_network", ip: "192.168.6.2", hostname: true
    nginx.vm.synced_folder ".", "/vagrant", disabled: true
    nginx.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  config.vm.define "kafka" do |kafka|
    kafka.vm.box = "ubuntu/focal64"
    kafka.vm.hostname = "kafka"
    kafka.vm.network "private_network", ip: "192.168.6.3", hostname: true
    kafka.vm.synced_folder ".", "/vagrant", disabled: true
    kafka.vm.provider "virtualbox" do |v|
      v.memory = 3072
      v.cpus = 1
    end
  end

  config.vm.define "wordpress" do |wordpress|
    wordpress.vm.box = "ubuntu/focal64"
    wordpress.vm.hostname = "wordpress"
    wordpress.vm.network "private_network", ip: "192.168.6.5", hostname: true
    wordpress.vm.synced_folder ".", "/vagrant", disabled: true
    wordpress.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 1
    end
  end

  config.vm.define "elk" do |elk|
    elk.vm.box = "ubuntu/focal64"
    elk.vm.hostname = "elk"
    elk.vm.network "private_network", ip: "192.168.6.4", hostname: true
    elk.vm.synced_folder ".", "/vagrant", disabled: true
    elk.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 1
    end
  end

end
