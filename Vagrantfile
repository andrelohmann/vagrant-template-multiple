# -*- mode: ruby -*-
# vi: set ft=ruby :

#require necessary plugins
required_plugins = %w( vagrant-hostmanager vagrant-vbguest )
required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true

  config.vm.define "box1" do |b|
    b.vm.box = "debian/jessie64"
    b.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = "1"
    end
    b.vm.synced_folder ".", "/vagrant", disabled: true
    b.vm.synced_folder "ansible", "/vagrant/ansible", create: true, owner: "vagrant", group: "vagrant", mount_options: ["dmode=777,fmode=777"]
    b.vbguest.auto_update = true

    b.vm.network "private_network", ip: "192.168.233.151"
    #b.vm.network "private_network", type: "dhcp"
    b.vm.hostname = "node1.local.dev"
    #b.hostmanager.aliases = %w(node-1.local.dev)

    b.vm.provision "ansible_local" do |ansible|
      ansible.install = true
      ansible.install_mode = :pip
      ansible.version = "latest"
      ansible.playbook = "ansible/box1/playbook.yml"
    end
  end

  config.vm.define "box2" do |b|
    b.vm.box = "debian/jessie64"
    b.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = "1"
    end
    b.vm.synced_folder ".", "/vagrant", disabled: true
    b.vm.synced_folder "ansible", "/vagrant/ansible", create: true, owner: "vagrant", group: "vagrant", mount_options: ["dmode=777,fmode=777"]
    b.vbguest.auto_update = true

    b.vm.network "private_network", ip: "192.168.233.152"
    #b.vm.network "private_network", type: "dhcp"
    b.vm.hostname = "node2.local.dev"
    #b.hostmanager.aliases = %w(node-2.local.dev)

    b.vm.provision "ansible_local" do |ansible|
      ansible.install = true
      ansible.install_mode = :pip
      ansible.version = "latest"
      ansible.playbook = "ansible/box2/playbook.yml"
    end
  end

  config.vm.define "box3" do |b|
    b.vm.box = "debian/jessie64"
    b.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = "1"
    end
    b.vm.synced_folder ".", "/vagrant", disabled: true
    b.vm.synced_folder "ansible", "/vagrant/ansible", create: true, owner: "vagrant", group: "vagrant", mount_options: ["dmode=777,fmode=777"]
    b.vbguest.auto_update = true

    b.vm.network "private_network", ip: "192.168.233.153"
    #b.vm.network "private_network", type: "dhcp"
    b.vm.hostname = "node3.local.dev"
    #b.hostmanager.aliases = %w(node-3.local.dev)

    b.vm.provision "ansible_local" do |ansible|
      ansible.install = true
      ansible.install_mode = :pip
      ansible.version = "latest"
      ansible.playbook = "ansible/box3/playbook.yml"
    end
  end
end
