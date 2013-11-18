Vagrant.configure("2") do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise-server-cloudimg-amd64-vagrant-disk1"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.hostname = "shopbox-thumbor"

  # config.vm.network :private_network, ip: "192.168.33.10"

  # config.vm.synced_folder "..", "/home/vagrant/shop", :nfs => true, :map_gid => 0, :map_uid => 0
  
  # config.vm.synced_folder "/Volumes/dev/dumps", "/home/vagrant/dumps" if File.exist?('/Volumes/dev/dumps')

  # config.ssh.forward_agent = true

  # Install chef if not available
  config.vm.provision :shell, path: "chef-install.sh"

  # config.vm.provision :shell do |shell|
    # shell.inline = "touch $1 && chmod 0440 $1 && echo $2 > $1"
    # shell.args = %q{/etc/sudoers.d/root_ssh_agent "Defaults    env_keep += \"SSH_AUTH_SOCK\""}
  # end

  # config.vm.provider :virtualbox do |vb|
    # Use VBoxManage to customize the VM. For example to change memory:
    # vb.customize ["modifyvm", :id, "--memory", "2304"] # 2.25GB
    # vb.customize ["modifyvm", :id, "--largepages", "on"]
    # vb.customize ["modifyvm", :id, "--cpus",
      # `sysctl hw.ncpu | awk '{print $2}'`.chomp
    # ]
  # end

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
    chef.add_recipe "zanui-thumbor"

    chef.run_list = ['recipe[apt]', 'recipe[nginx]', 'recipe[curl]']
    #chef.run_list = ['recipe[apt]', 'recipe[nginx]', 'recipe[curl]', 'recipe[zanui-thumbor]']
    #chef.run_list = ['recipe[zanui-thumbor]']

  end

end
