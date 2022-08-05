# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. 
  config.vm.network "forwarded_port", guest: 80, host: 8090
  config.vm.network "forwarded_port", guest: 443, host: 8449
  config.vm.network "forwarded_port", guest: 4000, host: 4009
  config.vm.network "forwarded_port", guest: 5000, host: 5003
  config.vm.network "forwarded_port", guest: 8080, host: 8009
  config.vm.network "forwarded_port", guest: 3389, host: 3399
  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.56.200", :adapter => 2
  config.vm.synced_folder "~/vagrant-data", "/vagrant-data", create: true
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
    #  vb.gui = true
     vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
     vb.customize [
            "modifyvm", :id,
            "--clipboard", "bidirectional",   # Sharing clipboard
            "--draganddrop", "bidirectional" # Enable D&D
        ]
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "4096"
  end
  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "build-vm.yml"
    ansible.verbose = "v"
  end
  config.ssh.forward_agent    = true
  config.ssh.insert_key       = true
end