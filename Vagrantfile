#box	= 'precise64'
#url	= 'http://files.vagrantup.com/precise64.box'
ram = '2048'

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


config.vm.box = "hashicorp/precise32"
config.vm.synced_folder "/Users/francescoparis/Documents/progetto/sinc", "/cartella", :mount_options => ["dmode=777", "fmode=777"]

config.vm.define "client" do |client|
    client.vm.hostname = "client" 
  	client.vm.network "private_network", ip: "192.168.50.101", virtualbox__intnet: true
  	
  	client.ssh.forward_agent = true
  	client.ssh.forward_x11 = true
 
 	client.vm.provision :chef_solo do |chef|
      chef.add_recipe "apt"
      chef.add_recipe "java"
      
      chef.json = {
        :java => {
          :jdk_version => '7'
        }
      }
  	end

 
  client.vm.provision :shell, :inline => "echo  'configurazione client completata'"
  end



#begin server
config.vm.define "server" do |server|
    server.vm.hostname = "server"
  	server.vm.network "private_network", ip: "192.168.50.102", virtualbox__intnet: true
	server.vm.network "forwarded_port", guest: 8080, host: 8080
	server.vm.network "forwarded_port", guest: 4848, host: 4848
	
	server.vm.provider "virtualbox" do |vb|
		vb.customize [
			'modifyvm', :id,
			'--memory', ram
		]
	end
	
	server.vm.provision "puppet" do |puppet|
		puppet.manifests_path = 'puppet/manifests'
		puppet.manifest_file = 'site.pp'
		puppet.module_path = 'puppet/modules'
	end
	
end

end