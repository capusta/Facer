
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "facer"
  config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |v|
    v.name = "facer"
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision :shell, :inline => "sudo rm /etc/localtime && sudo ln -s /usr/share/zoneinfo/America/Los_Angeles /etc/localtime", run: "always"

  config.vm.network "forwarded_port", guest: 3000, host: 3000, id: 'app_http'

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.raw_arguments = ["-Dv"]
  end

  config.vm.provision "dev", type: "ansible_local" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.raw_arguments = ["-Dv -t dev"]
  end

end
