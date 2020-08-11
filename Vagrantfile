# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX_IP = "192.168.133.10"
BOX_CPU_COUNT = "2"
BOX_RAM_MB = "4096"

PODMAN_PORT = "31887"

Vagrant.configure("2") do |config|

  config.vm.box = "fedora/32-cloud-base"
  config.vm.hostname = "podhost"
  config.vm.network "private_network", ip: BOX_IP

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.cpus = BOX_CPU_COUNT
    vb.memory = BOX_RAM_MB
  end

  # Enable provisioning with Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.extra_vars = {
      "ansible_python_interpreter" => "/usr/bin/python3"
    }
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "provisioning/main.yml"
  end
  
end
