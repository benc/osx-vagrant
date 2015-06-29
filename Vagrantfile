Vagrant.configure("2") do |config|
  config.vm.box = "osx-yosemite"
  config.ssh.insert_key = false

  # Build blog platform
  config.vm.provider :vmware_fusion do |provider, override|
    provider.vmx["memsize"] = "1024"
    provider.vmx["mks.enable3d"] = "FALSE"
    provider.vmx["mks.vsync"] = "1"
    provider.gui = false
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "development_machine.yml"
    ansible.sudo = true
    ansible.host_key_checking = false
    ansible.verbose = 'v'
  end
end
