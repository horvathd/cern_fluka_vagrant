Vagrant.configure("2") do |config|
  config.vm.define "fluka"

  config.vm.box = "ubuntu/bionic64"
  config.vm.box_check_update = false
  config.vm.hostname = "fluka"

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./Fluka", "/fluka"

  config.ssh.forward_x11 = true
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |v|
    v.customize [ "setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1" ]
    v.memory = 2048
    v.cpus = 2

    v.customize ["modifyvm", :id, "--uart1", "0x03f8", "4"]
    v.customize ["modifyvm", :id, "--uartmode1", "file", "Console.log"]
  end

  config.vm.provision "shell", inline: <<-SHELL
    echo "export DISPLAY=10.0.2.2:0" > /etc/profile.d/vagrant.sh
  SHELL
end
