Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.box = "CentOS6"
  config.vm.box_url = "../CentOS-6.box"
  # config.vm.box_url = "http://cloud.centos.org/centos/6/vagrant/x86_64/images/CentOS-6.box"
  vagrant_folder = "/vagrant/playbooks"
  config.vm.synced_folder "../ansible/playbooks", vagrant_folder, :nfs => true
  config.vm.network :private_network, ip: "192.168.51.4"
  config.vm.network "forwarded_port", guest: 5600, host: 5600

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "#{vagrant_folder}/provision.yml"
    ansible.sudo = true
    ansible.verbose = "vvv"
  end

end
