# Vagrantfile
Vagrant.configure("2") do |config|
  
	# Use Arch Linux as the base VM
 	config.vm.box = "archlinux/archlinux"
  
  	config.vm.network "forwarded_port", guest: 5000, host: 5000
  
  	config.vm.provision "shell", inline: <<-SHELL
    		sudo pacman -Syu --noconfirm git nano vim python python-virtualenv python-pip
    
    		cd /home/vagrant
    
    		python -m venv flask_venv
    
    		source flask_venv/bin/activate
    
    		pip install Flask
    
    		cat <<EOF > hello.py
from flask import Flask
app = Flask(__name__)
@app.route('/')
def hello():
    	return '<p>Hello, World!</p>'
EOF
    
    		flask --app hello run --host=0.0.0.0 &
  	SHELL
end




