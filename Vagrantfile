# -*- mode: ruby -*- 
# vi: set ft=ruby :

OS = "rolling"
BOX_IMAGE = "kalilinux/#{OS}"
NODE_COUNT = 1

Vagrant.configure("2") do |config|
  (1..NODE_COUNT).each do |i|     
    config.vm.define "#{OS}-#{i}" do |subconfig|       
      subconfig.vm.box = BOX_IMAGE       
      subconfig.vm.hostname = "#{OS}-#{i}"
      subconfig.vm.network :private_network, ip: "192.168.56.#{i + 100}"     
    end
  end 
  config.vm.provision "ansible_local" do |a|
    a.playbook = "playbook.yml"
  end  
end
