Vagrant.configure("2") do |config|
    # Definir la máquina virtual con Ubuntu
    config.vm.box = "ubuntu/bionic64"
  
    # Asignar una IP estática a la máquina virtual
    config.vm.network "private_network", ip: "192.168.33.10"
  
    # Configurar la cantidad de memoria RAM y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Compartir la carpeta local con el servidor Apache
    config.vm.synced_folder "./html", "/var/www/html"
  
    # Provisionar la instalación de Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  