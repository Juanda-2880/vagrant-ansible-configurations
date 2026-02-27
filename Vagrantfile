# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/rocky9"
  
  # Servidor: IP Estática y provisión con Ansible
  config.vm.define "server" do |server|
    server.vm.hostname = "server.lab.local"
    # virtualbox__intnet crea una red L2 aislada ideal para pruebas de broadcast DHCP
    server.vm.network "private_network", ip: "192.168.33.10", virtualbox__intnet: "devsecops_lab"
    
    server.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end

    server.vm.provision "ansible" do |ansible|
      ansible.playbook = "site.yml"
      ansible.inventory_path = "inventory/hosts.ini"
      ansible.become = true
    end
  end

  # Cliente: Sin IP asignada por Vagrant para forzar petición DHCP
  config.vm.define "client" do |client|
    client.vm.hostname = "client.lab.local"
    # auto_config: false evita que Vagrant interfiera con su propio DHCP
    client.vm.network "private_network", auto_config: false, virtualbox__intnet: "devsecops_lab"
    
    client.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  end
end