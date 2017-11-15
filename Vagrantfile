Vagrant.configure("2") do |config|

  config.vm.define :alpha do |alpha|
    alpha.vm.hostname = "alpha"
    alpha.vm.box = "ubuntu/xenial64"

    alpha.vm.box_check_update = false

    alpha.vm.network "forwarded_port", guest: 80, host: 8081
    alpha.vm.network :public_network, ip: "172.16.0.200", netmask: "255.255.0.0", bridge: "en0: Wi-Fi (AirPort)"

    alpha.vm.provision :ansible do |ansible|
      ansible.playbook = "provision.yml"
    end

    alpha.vm.provider "virtualbox" do |vb|
      vb.cpus = "1"
      vb.memory = "256"
      vb.gui = false
    end
  end

  config.vm.define :beta do |beta|
    beta.vm.hostname = "beta"
    beta.vm.network "public_network", ip: "172.16.0.201", netmask: "255.255.0.0", bridge: "en0: Wi-Fi (AirPort)"
    beta.vm.box = "ubuntu/xenial64"
    beta.vm.box_check_update = false

    beta.vm.provision :ansible do |ansible|
      ansible.playbook = "provision.yml"
    end

   beta.vm.provider "virtualbox" do |vb|
      vb.cpus = "1"
      vb.memory = "256"
      vb.gui = false
    end
  end
end