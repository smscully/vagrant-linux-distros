# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Create list with settings for each virtual machine
  distros=[
      {
        :hostname => "rockylinux-9.4",
        :box => "bento/rockylinux-9.4",
        :ip => "172.16.10.10",
        :ssh_port => '2210'
      },
      {
        :hostname => "ubuntu-24.04",
        :box => "bento/ubuntu-24.04",
        :ip => "172.16.10.20",
        :ssh_port => '2220'
      },
      {
        :hostname => "debian-12.6",
        :box => "bento/debian-12.6",
        :ip => "192.16.10.30",
        :ssh_port => '2230'
      },
      {
        :hostname => "opensuse-leap-15.6",
        :box => "bento/opensuse-leap-15.6",
        :ip => "192.16.10.40",
        :ssh_port => '2240'
      }
    ]

  # Create virtual machines
  distros.each do |machine|
    config.vm.define machine[:hostname] do |node|
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]
      node.vm.network "private_network", ip: machine[:ip]
      node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"

      # Run Ansible playbook to upgrade packages
      node.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbook.yml"
      end

      # Apply Virtual Box settings
      node.vm.provider :virtualbox do |vb|
        vb.name = machine[:hostname]
        vb.gui = true
        vb.memory = "1024"
        vb.cpus = "1"
      end
    end
  end
end
