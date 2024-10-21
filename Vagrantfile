Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.define "master" do |master|
    master.vm.network "private_network", ip: "192.168.57.103"
    master.vm.provision "shell", 
      inline: <<-SHELL
        apt update
        apt install -y bind9 dnsutils

      SHELL
  end

config.vm.define "slave" do |slave|

  slave.vm.network "private_network", ip: "192.168.57.102"
  slave.vm.provision "shell",
    inline: <<-SHELL

    apt update
    apt install -y bind9

  SHELL

  end

end