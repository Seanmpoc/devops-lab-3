# Vagrantfile
Vagrant.configure("2") do |config|
  
	# Use Arch Linux as the base VM
 	config.vm.box = "archlinux/archlinux"
  
  	config.vm.network "forwarded_port", guest: 5000, host: 8080
  
  	config.vm.provision "shell", inline: <<-SHELL
    		sudo pacman -Syu --noconfirm git nano vim python python-virtualenv python-pip
    
    		cd /home/vagrant
    
    		python -m venv flask_venv
    
    		source flask_venv/bin/activate
    
    		pip install Flask
    
    	SHELL

	config.vm.provision "file", source: "hello.py", destination: "/home/vagrant/hello.py"

	config.vm.provision "shell", inline: <<-SHELL
		source /home/vagrant/flask_venv/bin/activate
    
    		flask --app home/vagrant/hello run --host=0.0.0.0 &
  	SHELL
end




