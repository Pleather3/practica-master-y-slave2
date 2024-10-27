Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"


  # Máquina Maestro
  config.vm.define "master" do |master|
    master.vm.hostname = "tierra.sistema.test"
    master.vm.network "private_network", ip: "192.168.57.103"
  end

  # Máquina Esclava
  config.vm.define "dnslave" do |dnslave|
    dnslave.vm.hostname = "venus.sistema.test"
    dnslave.vm.network "private_network", ip: "192.168.57.102"
  end
end