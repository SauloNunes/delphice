Vagrant.configure("2") do |config|
  config.vm.box = "saulonunes/delphice"
  config.vm.box_version = "1.0"
  
  config.vm.guest = :windows
  config.vm.communicator = :winrm      
  
  config.vm.network "private_network", type: "dhcp" 
  config.vm.network "forwarded_port", host: 33389, guest: 3389, id: "rdp", auto_correct: true

  config.ssh.password = "vagrant"
  config.ssh.username = "vagrant" 
  
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.synced_folder "app/", "/app"
  
  config.vm.provider "virtualbox" do |v|
	v.name = "DELPHICEX"
	v.gui = false  
    v.memory = 8192
	v.cpus = 2
	v.customize ["modifyvm", :id, "--vram", "256"]
	#--nictype<1-N> Am79C970A|Am79C973|82540EM|82543GC|82545EM|virtio
	v.default_nic_type = "82540EM"
  end
end

#PC NAME  = DELPHICE
#LOGIN    = DELPHICE\vagrant
#Password = vagrant
#Reactivate Windows(Run CMD As Administrator) => slmgr /rearm 