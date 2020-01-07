Vagrant.configure("2") do |config|
  config.vm.define "node1" do |node1|
    node1.vm.box = "ubuntu/bionic64"
    node1.vm.hostname = 'node1'
    node1.vm.box_url = "ubuntu/bionic64"

    node1.vm.network :private_network, ip: "192.168.56.101"
    node1.vm.network :forwarded_port, guest: 22, host: 10123, id: "ssh"

    node1.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "node1"]
    end
    node1.vm.provision :shell, path: "bootstrap.sh", args: "node1"
  end

  config.vm.define "node2" do |node2|
    node2.vm.box = "ubuntu/bionic64"
    node2.vm.hostname = 'node2'
    node2.vm.box_url = "ubuntu/bionic64"

    node2.vm.network :private_network, ip: "192.168.56.102"
    node2.vm.network :forwarded_port, guest: 22, host: 10223, id: "ssh"

    node2.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "node2"]
    end
    node2.vm.provision :shell, path: "bootstrap.sh", args: "node2"
  end

end