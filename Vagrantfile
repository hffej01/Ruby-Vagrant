# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

##  config.vm.box_check_update = true
    config.vm.define "centos1" do |centos1|
    centos1.vm.box = "centos/7"
    centos1.vm.provider "VirtualBox" do |vbcustom|

    unless File.exist? ('centos1.additional.vdi')
   vbcustom.customize ['createhd', '--filename','centos1.additional.vdi','--size', 2 * 1024]
 end
   vbcustom.customize ['storageattach', :id,'--storagectl','IDE','--port', 0,'--device',1, '--type','hdd','--medium','centos1.additional.vdi']

     unless File.exist? ('centos1.additional2.vdi')
   vbcustom.customize ['createhd', '--filename','centos1.additional2.vdi','--size', 2 * 1024]
 end
   vbcustom.customize ['storageattch', :id,'--storagectl','IDE','--port', 1, '--device' ,1,'--type','hdd','--medium','centos1.additional2.vdi']
 end

 config.vm.provision "shell", inline: <<-SHELL
   yum update
   yum install -y epel-release.noarch
 SHELL
  end
end
