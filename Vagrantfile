Vagrant.configure("2") do |config|
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.box = "precise64"

  config.vm.network :private_network, ip: "198.101.10.10"
  config.vm.hostname = "openstack.local"
  
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "devstack-chef"
  end

  cafe_cmd = "for i in opencafe cloudcafe cloudroast; do git clone https://github.com/stackforge/$i.git /opt/$i; sudo pip install -r /opt/$i/pip-requires; sudo pip install /opt/$i --upgrade; done"

  config.vm.provision :shell, :inline => [cafe_cmd].join('; ')
end
