# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "sql" do |sql|
    sql.vm.box = "centos/7"
    sql.vm.hostname = "sql"
    sql.vm.network "private_network", ip: "192.168.200.2"
    sql.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "sql.yml"
    end
    sql.vm.provision "shell", path: "scripts/createDB.sh"
  end

   config.vm.define "dns" do |dns|
    dns.vm.box = "centos/7"
    dns.vm.hostname = "dns"
    dns.vm.network "private_network", ip: "192.168.200.3"
    dns.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "dns.yml"
    end
  end

  config.vm.define "client" do |client|
    client.vm.box = "centos/7"
    client.vm.hostname = "client"
    client.vm.network "private_network", ip: "192.168.200.121"
    client.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "client.yml"
    end
  end
end