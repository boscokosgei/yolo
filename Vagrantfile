# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Define the box to be used for the VM
  config.vm.box = "ubuntu/jammy64"

  # Forward port 8000 on the host to port 8000 on the guest.
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  # Install Docker on the VM
  config.vm.provision "shell", inline: <<-SHELL
    # Update and install prerequisites
    sudo apt-get update
    sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

    # Add Docker’s official GPG key and repository
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

    # Install Docker
    sudo apt-get update
    sudo apt-get install -y docker-ce

    # Add the vagrant user to the docker group to avoid permission issues
    sudo usermod -aG docker vagrant

    # Enable Docker service to start on boot
    sudo systemctl enable docker
  SHELL

  # Provisioning configuration for Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yaml"
  end

  # Optional provider-specific configuration (e.g., for VirtualBox).
  # Uncomment and customize as needed:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   vb.gui = true  # Display VirtualBox GUI
  #   vb.memory = "1024"  # Set memory size
  # end
end