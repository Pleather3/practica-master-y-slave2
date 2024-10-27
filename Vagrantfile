Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  # Máquina Maestro
  config.vm.define "master" do |master|
    master.vm.hostname = "tierra.sistema.test"
    master.vm.network "private_network", ip: "192.168.57.103"
    
    master.vm.provision "shell", name: "update_master", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y bind9
      cp -v /vagrant/named /etc/default/named
      sudo systemctl restart named
      cp -v /vagrant/named.conf.options /etc/bind/named.conf.options
      sudo systemctl restart bind9
    SHELL
  end

  # Máquina Esclava
  config.vm.define "dnslave" do |dnslave|
    dnslave.vm.hostname = "venus.sistema.test"
    dnslave.vm.network "private_network", ip: "192.168.57.102"
    
    dnslave.vm.provision "shell", name: "update_slave", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y bind9
      cp -v /vagrant/named /etc/default/named
      sudo systemctl restart named
      cp -v /etc/bind/named.conf.options /vagrant/named.conf.options
      sudo systemctl restart bind9
    SHELL
  end
end