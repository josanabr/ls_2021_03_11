Vagrant.configure("2") do |config|
  config.vm.define "haproxy" do |m|
      m.vm.box = "ubuntu/bionic64"
      m.vm.hostname = "haproxy"
      m.vm.network "forwarded_port", guest: 80, host: 8080
      m.vm.network "private_network", ip: "192.168.33.10"
      m.vm.provider :virtualbox do |vb|
        vb.customize [ 'modifyvm', :id, '--memory', '1024' ]
        vb.customize [ 'modifyvm', :id, '--name', 'haproxy' ]
      end
  end
  config.vm.define "web1" do |m|
      m.vm.box = "ubuntu/xenial64"
      m.vm.hostname = "web1"
      m.vm.provision "shell", path: "install-apache.sh"
      m.vm.synced_folder "./web1", "/var/www/html"
      m.vm.network "private_network", ip: "192.168.33.11"
      m.vm.provider :virtualbox do |vb|
        vb.customize [ 'modifyvm', :id, '--memory', '512' ]
        vb.customize [ 'modifyvm', :id, '--name', 'web1' ]
      end
  end
  config.vm.define "web2" do |m|
      m.vm.box = "ubuntu/xenial64"
      m.vm.hostname = "web2"
      m.vm.provision "shell", path: "install-apache.sh"
      m.vm.synced_folder "./web2", "/var/www/html"
      m.vm.network "private_network", ip: "192.168.33.12"
      m.vm.provider :virtualbox do |vb| 
        vb.customize [ 'modifyvm', :id, '--memory', '512' ]
        vb.customize [ 'modifyvm', :id, '--name', 'web2' ]
      end
  end
end
