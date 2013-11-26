Vagrant.configure("2") do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise-server-cloudimg-amd64-vagrant-disk1"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.hostname = "shopbox-thumbor"

  # Install chef if not available
  config.vm.provision :shell, path: "chef-install.sh"

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  config.vm.provision :chef_solo do |chef|
    chef.log_level = :debug
    chef.cookbooks_path = "./thumbor-cookbooks"
    #tbr
    chef.add_recipe "apt"
    chef.add_recipe "nginx"
    chef.add_recipe "curl"
    chef.add_recipe "python"
    chef.add_recipe "zanui-thumbor"

    chef.run_list = ['recipe[apt]', 'recipe[nginx]', 'recipe[curl]', 'recipe[python]', 'recipe[zanui-thumbor]']
    #chef.run_list = ['recipe[zanui-thumbor]']

  end

end
