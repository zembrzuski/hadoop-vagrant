
def config_machine (config, machine_name, playbook_yml, ip)
  config.vm.define machine_name do |node|
    node.vm.provider :virtualbox do |v|
      v.name = machine_name
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.memory = 1024
      v.cpus = 2
    end
    node.vm.network "private_network", ip: ip
    node.vm.hostname = machine_name

    node.vm.provision :hostmanager

    config.vm.provision "ansible" do |ansible|
     ansible.playbook = playbook_yml
     ansible.extra_vars = {
       my_machine: machine_name
     }
    end
  end
end


Vagrant.configure(2) do |config|

  config.vm.box = "hashicorp/precise64"

  # https://github.com/devopsgroup-io/vagrant-hostmanager
  config.hostmanager.enabled = false
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true
  config.hostmanager.ignore_private_ip = false

  config_machine(config, "master", "playbook-master.yml", "192.168.56.11")
  config_machine(config, "slave1", "playbook-slave.yml",  "192.168.56.12")

end