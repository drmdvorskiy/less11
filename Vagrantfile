Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
  end

  config.vm.provision "file", source: "key/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
  config.vm.provision "shell", inline: <<-SHELL
    cat /home/vagrant/.ssh/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL

  config.vm.define "nginx" do |nginx|
    nginx.vm.box = "ubuntu/focal64"
    nginx.vm.hostname = "nginx"
    nginx.vm.network "private_network", ip: "192.168.6.2", hostname: true
    nginx.vm.synced_folder ".", "/vagrant", disabled: true
  end

  config.vm.define "kafka" do |kafka|
    kafka.vm.box = "ubuntu/focal64"
    kafka.vm.hostname = "kafka"
    kafka.vm.network "private_network", ip: "192.168.6.3", hostname: true
    kafka.vm.synced_folder ".", "/vagrant", disabled: true
  end

  config.vm.define "elk" do |elk|
    elk.vm.box = "ubuntu/focal64"
    elk.vm.hostname = "elk"
    elk.vm.network "private_network", ip: "192.168.6.4", hostname: true
    elk.vm.synced_folder ".", "/vagrant", disabled: true
  end

end
