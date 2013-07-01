Vagrant.configure("2") do |config|
  config.vm.network :private_network, ip: "198.101.10.10"
  config.vm.hostname = "openstack.local"
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "devstack-chef"
    chef.add_recipe "cloudcafe"
  end
end
