Vagrant.configure("2") do |config|
  # Настройка для первой ВМ
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "debian/bookworm64" # Официальный образ Debian
    vm1.vm.hostname = "vm1"
    vm1.vm.network "private_network", ip: "192.168.56.10"
    # Настройка RSync для общих папок
    vm1.vm.synced_folder "./shared", "/vagrant_shared", type: "rsync"
    # Провизия: копирование файла
    vm1.vm.provision "file", source: "./example.txt", destination: "example.txt"
  end

  # Настройка для второй ВМ
  config.vm.define "vm2" do |vm2|
    vm2.vm.box = "debian/bookworm64"
    vm2.vm.hostname = "vm2"
    vm2.vm.network "private_network", ip: "192.168.56.20"
    vm2.vm.synced_folder "./shared", "/vagrant_shared", type: "rsync"
    vm2.vm.provision "file", source: "./example.txt", destination: "example.txt"
  end
end
