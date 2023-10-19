Vagrant.configure("2") do |config|
    config.vm.define "master" do | master |    
    master.vm.box = "jacobw/fedora35-arm64"
    master.vm.network "private_network", ip: "192.168.56.27"
    master.vm.hostname = "master"
    master.vm.provider "vmware_desktop" do |v|
      v.allowlist_verified = true
      v.ssh_info_public = true
        v.gui = true
    end
    master.vm.provision "shell", inline: <<-SHELL
     mv /etc/yum.repos.d/fedora-updates.repo /tmp/
     mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
     yum clean all
     yum update
     systemctl stop firewalld
    SHELL
  end
    config.vm.define "slave" do |slave|    
    slave.vm.box = "jacobw/fedora35-arm64"
    slave.vm.network "private_network", ip: "192.168.56.28"
    slave.vm.hostname = "slave"
    slave.vm.provider "vmware_desktop" do |v|
      v.allowlist_verified = true
      v.ssh_info_public = true
        v.gui = true
    end
    slave.vm.provision "shell", inline: <<-SHELL
     mv /etc/yum.repos.d/fedora-updates.repo /tmp/
     mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
     yum clean all
     yum update
     systemctl stop firewalld
    SHELL
  end
end
