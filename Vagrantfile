$scriba = <<SCRIPT
mkdir /tmp/gitti && cd /tmp/gitti
git clone git://osoite.jotain/

SCRIPT

Vagrant.configure("2") do |config|
  config.vm.define :test_vm do |test_vm|
    config.vm.hostname = "test-vm"
    config.vm.network "private_network", ip: "192.168.125.253"
    config.vm.network "public_network"
    test_vm.vm.box = "fjb/precise64-libvirt"

    config.vm.synced_folder ".", "/vagrant", disabled: true
    config.vm.provision :shell, :inline =>  $scriba

    test_vm.vm.provider :libvirt do |domain|
      domain.cpus = 2
      domain.machine_virtual_size = 10
      domain.memory = 256
  end
end
