Vagrant.configure("2") do |config|
  # Use bento/ubuntu-22.04 box, which includes VirtualBox Guest Additions
  config.vm.box = "bento/rockylinux-8"

  # Disable vagrant-vbguest to avoid conflicts if plugin is installed
  config.vbguest.auto_update = false if Vagrant.has_plugin?("vagrant-vbguest")

  # Common settings for all VMs
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus = 1
  end

  # Controller node
  config.vm.define "controller", primary: true do |controller|
    controller.vm.hostname = "controller"
    controller.vm.network "private_network", ip: "192.168.56.10"
    controller.vm.synced_folder "/home/joshua/Desktop/AnsibleProject/ProjectNginx/Vagrant", "/home/vagrant/project"

    controller.vm.provision "shell", inline: <<-SHELL
      sudo dnf update
      sudo dnf install epel-release -y
      sudo dnf install ansible -y
      sudo echo "mypassword" | passwd --stdin vagrant
    SHELL
  end

  # Slave node 1
  config.vm.define "slave1" do |slave1|
    slave1.vm.hostname = "slave1"
    slave1.vm.network "private_network", ip: "192.168.56.11"

    slave1.vm.provision "shell", inline: <<-SHELL
      sudo dnf update -y
      sudo dnf install -y openssh-server python3
      sudo systemctl enable ssh.service
      sudo systemctl start ssh.service
      sudo echo "mypassword" | passwd --stdin vagrant
    SHELL
  end

  # Slave node 2
  config.vm.define "slave2" do |slave2|
    slave2.vm.hostname = "slave2"
    slave2.vm.network "private_network", ip: "192.168.56.12"

    slave2.vm.provision "shell", inline: <<-SHELL
      sudo dnf update -y
      sudo dnf install -y openssh-server python3
      sudo systemctl enable ssh.service
      sudo systemctl start ssh.service
      sudo echo "mypassword" | passwd --stdin vagrant
    SHELL
  end

    # Slave node 3
  config.vm.define "slave3" do |slave3|
    slave3.vm.hostname = "slave3"
    slave3.vm.network "private_network", ip: "192.168.56.13"

    slave3.vm.provision "shell", inline: <<-SHELL
      sudo dnf update -y
      sudo dnf install -y openssh-server python3
      sudo systemctl enable ssh.service
      sudo systemctl start ssh.service
      sudo echo "mypassword" | passwd --stdin vagrant
    SHELL
  end
end

