# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.network :forwarded_port, guest: 80, host: 10080
  config.vm.network :forwarded_port, guest: 9200, host: 19200
  config.vm.network :forwarded_port, guest: 5601, host: 15601
  config.vm.synced_folder "/tmp/artifacts", "/tmp/artifacts", create: true
  config.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "/etc/ansible/hosts"
        ansible.playbook = "ansible/playbooks/install-all.yml"
        #ansible.playbook = "ansible/playbooks/test.yml"
        ansible.verbose = "vvvv"
        ansible.limit = "all"
  end
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2000"]
  end
end
