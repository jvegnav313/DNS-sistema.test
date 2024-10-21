Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.define "master" do |master|
    master.vm.network "private_network", ip: "192.168.57.103"
    master.vm.provision "shell", 
      inline: <<-SHELL
        apt update
        apt install -y bind9 dnsutils

        cp -v /vagrant/master/named /etc/default
        cp -v /vagrant/master/named.conf.local /etc/bind
        cp -v /vagrant/master/named.conf.options /etc/bind
        cp -v /vagrant/master/sistema.test.dns /var/lib/bind
        cp -v /vagrant/master/sistema.test.rev /var/lib/bind


        systemctl restart bind9

      SHELL
  end

config.vm.define "slave" do |slave|

  slave.vm.network "private_network", ip: "192.168.57.102"
  slave.vm.provision "shell",
    inline: <<-SHELL

    apt update
    apt install -y bind9

    cp -v /vagrant/slave/named /etc/default
    cp -v /vagrant/slave/named.conf.local /etc/bind

  SHELL

  end

end