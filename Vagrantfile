require 'yaml'

Vagrant.configure("2") do |config|
  config.vm.box = "yosemite"
  config.ssh.insert_key = false
  # config.ssh.private_key_path = ["#{ENV['HOME']}/.ssh/id_rsa","#{ENV['HOME']}/.vagrant.d/insecure_private_key"]

  # Build blog platform
  config.vm.provider :vmware_fusion do |provider, override|
    provider.vmx["memsize"] = "1024"
    provider.vmx["mks.enable3d"] = "FALSE"
    provider.vmx["mks.vsync"] = "1"
    provider.gui = false
  end

  # config.vm.provision :shell, inline: <<-SCRIPT
  #   printf "%s\n" "#{File.read("#{ENV['HOME']}/.ssh/id_rsa.pub")}" > /home/vagrant/.ssh/authorized_keys
  #   chown -R vagrant:vagrant /home/vagrant/.ssh
  # SCRIPT

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "development_machine.yml"
    ansible.sudo = true
    ansible.host_key_checking = false
    ansible.verbose = 'v'
  end
end
