Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.network "public_network", type: "dhcp"

  config.vm.network "forwarded_port", guest: 82, host: 8080

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y nginx
    sudo sed -i 's/listen 80 default_server;/listen 82 default_server;/g' /etc/nginx/sites-available/default
    sudo systemctl restart nginx
	
    echo 'Welcome Back My Lord' | sudo tee /var/www/html/index.nginx-debian.html > /dev/null
  SHELL
end