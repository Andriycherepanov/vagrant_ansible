Vagrant.configure("2") do |config|

# Web server 1 configuration
  config.vm.define "web01" do |w1|
    w1.vm.box = "bento/centos-7.2"
    w1.vm.hostname = "web01"
    w1.vm.box_url = "bento/centos-7.2"
    w1.vm.network :private_network, ip: "192.168.10.110"
    w1.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    w1.vm.provision "shell",
      inline: "sudo ifup enp0s8"
  end
  
# Web server 2 configuration 
  config.vm.define "web02" do |w2|
    w2.vm.box = "bento/centos-7.2"
    w2.vm.hostname = "web02"
    w2.vm.box_url = "bento/centos-7.2"
    w2.vm.network :private_network, ip: "192.168.10.111"
    w2.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
	w2.vm.provision "shell",
      inline: "sudo ifup enp0s8"
  end
  
# Haproxy configuration  
  config.vm.define "ha1" do |w3|
    w3.vm.box = "bento/centos-7.2"
    w3.vm.hostname = "ha1"
    w3.vm.box_url = "bento/centos-7.2"
    w3.vm.network :private_network, ip: "192.168.10.112"
    w3.vm.network :forwarded_port, guest: 80, host: 8082, id: "http"
    w3.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    w3.vm.provision "shell",
      inline: "sudo ifup enp0s8"
  end
  
# Ecinga monitoring service
  config.vm.define "ecinga1" do |w4|
    w4.vm.box = "bento/centos-7.2"
    w4.vm.hostname = "ecinga1"
    w4.vm.box_url = "bento/centos-7.2"
    w4.vm.network :private_network, ip: "192.168.10.113"
    w4.vm.network :forwarded_port, guest: 80, host: 8080, id: "http"
    w4.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
	w4.vm.provision "shell",
      inline: "sudo ifup enp0s8"
	  
# Ansible part	
	w4.vm.provision "ansible_local" do |ansible|
      ansible.playbook       = "provisioning/playbook.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all"
      ansible.inventory_path = "provisioning/inventory"
	end
  end 
end
