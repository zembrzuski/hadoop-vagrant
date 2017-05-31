Vagrant.configure(2) do |config|

  # Define base image
  config.vm.box = "hashicorp/precise64"

  # copiei e colei. nao sei para que serve ao certo. estou confiando.
  # Manage /etc/hosts on host and VMs
  # documentacao estah em 
  # https://github.com/devopsgroup-io/vagrant-hostmanager
  config.hostmanager.enabled = false
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true
  config.hostmanager.ignore_private_ip = false

  config.vm.define :master do |master|

    puts :master
    puts :master
    puts :master
    puts :master
    puts :master
    puts :master
    puts :master
    puts :master
    puts :master
    puts :master

    master.vm.provider :virtualbox do |v|
      v.name = "master"
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.memory = 512
      v.cpus = 2
    end
    master.vm.network "private_network", ip: "192.168.56.11"
    master.vm.hostname = "master"

    master.vm.provision :hostmanager

    config.vm.provision "ansible" do |ansible|
     ansible.playbook = "playbook-master.yml"
     ansible.extra_vars = {
       my_machine: :master
     }
    end
  end

  # config.vm.define :slave_one do |slave_one|
  #   slave_one.vm.provider :virtualbox do |v|
  #     v.name = "slave1"
  #     v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  #     v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  #     v.memory = 512
  #     v.cpus = 2
  #   end
  #   slave_one.vm.network "private_network", ip: "192.168.56.12"
  #   slave_one.vm.hostname = "slave1"
  #
  #   slave_one.vm.provision :hostmanager
  #
  #   config.vm.provision "ansible" do |ansible|
  #    ansible.playbook = "playbook-slave.yml"
  #   end
  # end

end