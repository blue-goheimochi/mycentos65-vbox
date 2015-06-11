VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos65-x86_64-20131205"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.1/centos65-x86_64-20131205.box"

  # Set the VirtualBox Configration
  config.vm.provider "virtualbox" do |vb|
    # Change memory size
    vb.customize ["modifyvm", :id, "--memory", 1024]
  end

  # Install chef
  config.vm.provision :shell, :inline => "curl -L 'https://www.getchef.com/chef/install.sh' | sudo bash"

  # provisioning with chef solo.
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["./provision/chef/cookbooks","./provision/chef/site-cookbooks"]
    chef.add_recipe "chkconfig"
    chef.add_recipe "selinux"
    chef.add_recipe "yum"
    chef.add_recipe "ntp"
    chef.add_recipe "nkf"
    chef.add_recipe "remi"
    chef.add_recipe "rpmforge"
    chef.add_recipe "epel"
  end

end
