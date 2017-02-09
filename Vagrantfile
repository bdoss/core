# For a complete reference, please see the online documentation at
# https://docs.vagrantup.com.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8088" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 8088, host: 8088, auto_correct: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  #
  config.vm.provider "virtualbox" do |vb|
    # Name of virtual machine as shown in vbox:
    vb.name = "dotnet 1.0-preview2.1"
    # Customize the amount of memory on the VM:
    vb.memory = "512"
  end
  
  # dotnet core sdk install reference: https://www.microsoft.com/net/core#linuxubuntu
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    echo "Provisioning Virtual Machine..."
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893
    
    sudo apt-get update

    sudo apt-get install dotnet-dev-1.0.0-preview2.1-003177 -y
  SHELL
end
