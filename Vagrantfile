# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "devbox"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:5080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 5080, host: 5080, auto_correct: true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/home/vagrant/hostbox"

  config.vm.provider :virtualbox do |v|
    # Setting VM name and increasing RAM size
    v.customize [
      "modifyvm", :id,
      "--memory", "2048",
      "--name", "devbox"
    ]
    # Boot with a GUI so you can see the screen. (Default is headless)
    # v.gui = true

    # without this symlinks can't be created on the shared folder
    v.customize [
      "setextradata", :id,
      "VBoxInternal2/SharedFoldersEnableSymlinksCreate/app", "1"
    ]
  end

  config.vm.provision "ansible" do |a|
    a.playbook = "playbook.yml"
    # Run commands as root.
    a.sudo = true
  end

end

