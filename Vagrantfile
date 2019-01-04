Vagrant.configure("2") do |config|
    
    config.vm.box = "ubuntu/trusty64"
    config.vm.provider "virtualbox" do |v|
        v.memory = 3000
    end

    config.vm.define "ra" do |ra_config|
        ra_config.vm.network "private_network", ip: "172.16.0.10"
        ra_config.vm.provision "shell", inline: <<-SHELL
           sudo apt-get update
           sudo apt-get install -y software-properties-common curl apt-transport-https ca-certificates linux-image-extra-$(uname -r) linux-image-extra-virtual
           curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
           sudo apt-key fingerprint 0EBFCD88
           sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
           sudo apt-get update
           sudo apt-get install -y docker-ce
        SHELL
    end
end
