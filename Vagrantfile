# -*- mode: ruby -*-
# vi: set ft=ruby :

VM_NAME="dev.coreos"
VM_HOSTNAME="dev.coreos"
PRIVATE_IP="192.168.33.101"
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # coreOS base setting
  config.vm.box = "coreos-alpha"
  config.vm.box_url = "https://storage.googleapis.com/alpha.release.core-os.net/amd64-usr/current/coreos_production_vagrant.json"
  config.ssh.insert_key = false
  config.vm.hostname = VM_HOSTNAME
  config.vm.network :private_network, :ip => PRIVATE_IP
  config.vm.synced_folder "../../share", "/home/core/share", :nfs => true, :mount_options => ["nolock,vers=3,udp"]

  # VitutalBox
  config.vm.provider "virtualbox" do |vb|
    vb.name = VM_NAME
    vb.cpus = "2"
    vb.memory = "4096"
    vb.check_guest_additions = false
    vb.functional_vboxsf     = false
  end

  # for keep vbguest-GuestOS compatibility
  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end

  # docker-compose install
  config.vm.provision :shell, inline: <<-SHELL
    mkdir -p /opt/bin
    curl -L https://github.com/docker/compose/releases/download/1.12.0/docker-compose-`uname -s`-`uname -m` > /opt/bin/docker-compose
    chmod +x /opt/bin/docker-compose
  SHELL


end
