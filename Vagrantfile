# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant_API_Version ="2"

Vagrant.configure(Vagrant_API_Version) do |config|

  #==============#
  # Ubuntu nodes #
  #==============#
  
  #Ansible-Node101	 
  config.vm.define:"ansible-node101" do |cfg|
    cfg.vm.box = "ubuntu/trusty64"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-node101(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node101"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.101"
			cfg.vm.network "forwarded_port", guest: 22, host: 60101, auto_correct: false, id: "ssh"
  end  
  
  #Ansible-Node102	 
  config.vm.define:"ansible-node102" do |cfg|
    cfg.vm.box = "ubuntu/trusty64"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node102(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node102"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.102"
			cfg.vm.network "forwarded_port", guest: 22, host: 60102, auto_correct: false, id: "ssh"
  end

  #Ansible-Node103	 
  config.vm.define:"ansible-node103" do |cfg|
		cfg.vm.box = "ubuntu/trusty64"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node103(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node103"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.103"
			cfg.vm.network "forwarded_port", guest: 22, host: 60103, auto_correct: false, id: "ssh"
  end  

  #Ansible-Node104	 
  config.vm.define:"ansible-node104" do |cfg|
		cfg.vm.box = "ubuntu/trusty64"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node104(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node104"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.104"
			cfg.vm.network "forwarded_port", guest: 22, host: 60104, auto_correct: false, id: "ssh"
  end  

  #==============#
  # CentOS nodes #
  #==============#
  
  #Ansible-Node201	 
  config.vm.define:"ansible-node201" do |cfg|
		cfg.vm.box = "centos/7"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node201(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node201"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.201"
			cfg.vm.network "forwarded_port", guest: 22, host: 60201, auto_correct: false, id: "ssh"
			cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
  end

  #Ansible-Node202	 
  config.vm.define:"ansible-node202" do |cfg|
		cfg.vm.box = "centos/7"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node202(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node202"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.202"
			cfg.vm.network "forwarded_port", guest: 22, host: 60202, auto_correct: false, id: "ssh"
			cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
  end  

  #Ansible-Node203	 
  config.vm.define:"ansible-node203" do |cfg|
		cfg.vm.box = "centos/7"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node203(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node203"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.203"
			cfg.vm.network "forwarded_port", guest: 22, host: 60203, auto_correct: false, id: "ssh"
			cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
  end  

  #Ansible-Node204	 
  config.vm.define:"ansible-node204" do |cfg|
		cfg.vm.box = "centos/7"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Node204(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-node204"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.204"
			cfg.vm.network "forwarded_port", guest: 22, host: 60204, auto_correct: false, id: "ssh"
			cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
  end  

  #================#
  # Ansible Server #
  #================#
  
  config.vm.define:"ansible-server" do |cfg|
		cfg.vm.box = "centos/7"
			cfg.vm.provider:virtualbox do |vb|
				vb.name="Ansible-Server(github_SysNet4Admin)"
			end
			cfg.vm.host_name="ansible-server"
			cfg.vm.synced_folder ".", "/vagrant", disabled: true
			cfg.vm.network "public_network", ip: "192.168.219.10"
			cfg.vm.network "forwarded_port", guest: 22, host: 60010, auto_correct: false, id: "ssh"

			# 프로비저닝 설정
			cfg.vm.provision "shell", path: "bootstrap.sh"
			cfg.vm.provision "file", source: "Ansible_env_ready.yml", destination: "Ansible_env_ready.yml"
			cfg.vm.provision "shell", inline: "ansible-playbook Ansible_env_ready.yml"
			cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
			cfg.vm.provision "file", source: "Auto_known_host.yml", destination: "Auto_known_host.yml"
			cfg.vm.provision "shell", inline: "ansible-playbook Auto_known_host.yml", privileged: false	
			cfg.vm.provision "file", source: "Auto_authorized_keys.yml", destination: "Auto_authorized_keys.yml"
			cfg.vm.provision "shell", inline: "ansible-playbook Auto_authorized_keys.yml --extra-vars 'ansible_ssh_pass=vagrant'", privileged: false
			cfg.vm.provision "file", source: "nginx", destination: "nginx"
			cfg.vm.provision "file", source: "nfs", destination: "nfs"
			cfg.vm.provision "file", source: "handler", destination: "handler"
			cfg.vm.provision "file", source: "vars", destination: "vars"
			cfg.vm.provision "file", source: "template", destination: "template"
			cfg.vm.provision "file", source: "roles", destination: "roles"
			cfg.vm.provision "file", source: "ansible_galaxy_roles", destination: "ansible_galaxy_roles"
  end  
end
