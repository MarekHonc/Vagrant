# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "sql" do |sql|
    sql.vm.box = "centos/7"
    sql.vm.hostname = "sql"
    sql.vm.network "private_network", ip: "192.168.200.2", netmask: "24"
    sql.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "sql.yml"
    end
    sql.vm.provision "shell", path: "scripts/createDB.sh"
  end
end