# ---- Vagrant configuration ---- 
# ---- Configuration variables ---- 
GUI               = false # Enable/Disable GUI 
RAM               = 2000   # Default memory size in MB 
# Network configuration 
DOMAIN            = "devcnt67.local" 
NETWORK           = "10.0.0." 
NETMASK           = "255.255.255.0" 
BOX               = 'centos/7' 
#Hosts Definition
HOSTS = { 

   "vm1" => [NETWORK+"2", RAM, GUI, BOX], 

} 
Vagrant.configure(2) do |config| 

  HOSTS.each do | (name, cfg) | 

    ipaddr, ram, gui, box = cfg 
    config.vm.define name do |machine|

      machine.vm.box   = box 
      machine.vm.guest = :redhat 

        machine.vm.provider "virtualbox" do |vbox| 

          vbox.gui    = gui 
          vbox.memory = ram 
          vbox.name = name 

        end 

      machine.vm.hostname = name  
      machine.vm.network 'private_network', ip: ipaddr, netmask: NETMASK 

    end 
  end #endforeach

end 
