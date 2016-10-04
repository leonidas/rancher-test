# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "private_network", type: "dhcp"

  config.vm.provider :virtualbox do |virtualbox|
    virtualbox.cpus = 4
    virtualbox.memory = 2048
  end

  config.vm.define "default" do |default|
    default.vm.provision :ansible do |ansible|
      ansible.playbook = "rancher-test.yml"
      # ansible.vault_password_file = ".vault_pass.txt"
      ansible.extra_vars = {
      }
      ansible.groups = {
        "rancher-servers" => ["default"]
      }
      ansible.host_key_checking = false
    end
  end
end
