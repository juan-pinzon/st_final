Vagrant.configure("2") do |config|
	config.vm.define :server do |server|
		server.vm.box = "bento/centos-7.9"
		server.vm.network :private_network, ip: "192.168.160.2"
		server.vm.hostname = "server"
		server.vm.provision "shell", inline:<<-SHELL
			yum update -y
			yum install -y curl wget
			curl https://assets.nagios.com/downloads/nagiosxi/install.sh | sh
		SHELL
	end

	config.vm.define :ftp do |ftp|
		ftp.vm.box = "bento/centos-7.9"
		ftp.vm.network :private_network, ip: "192.168.160.3"
		ftp.vm.hostname = "ftp"
		ftp.vm.provision "shell", inline:<<-SHELL
			yum install vsftpd -y
			chkconfig vsftpd on
			service vsftpd start
		SHELL
	end
	
	config.vm.define :http do |http|
		http.vm.box = "bento/centos-7.9"
		http.vm.network :private_network, ip: "192.168.160.4"
		http.vm.hostname = "http"
		http.vm.provision "shell", inline:<<-SHELL
			yum install httpd -y
			chkconfig httpd on
			service httpd start
		SHELL
	end
	
	config.vm.define :cliente do |cliente|
		cliente.vm.box = "bento/centos-7.9"
		cliente.vm.network :private_network, ip: "192.168.160.5"
		cliente.vm.hostname = "cliente"
		cliente.vm.provision "shell", inline:<<-SHELL
			rpm -Uvh http://repo.nagios.com/nagios/7/nagios-repo-7-4.el7.noarch.rpm
			yum install ncpa -y
		SHELL
	end
end