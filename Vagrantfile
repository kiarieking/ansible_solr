Vagrant.configure("2") do |config|
    config.vm.box = "cdsn/debian13"

    config.ssh.insert_key = true

    config.vm.synced_folder ".", "/vagrant", disabled: true

    config.vm.provider :virtualbox do |v|
        v.memory = 256
        v.linked_clone = true
        v.customize ['createhd', '--filename', 'extra_disk.vdi', '--size', 2000]
        v.customize ['storageattach', :id,
                '--port', 1,
                '--device', 0,
                '--type', 'hdd',
                '--medium', 'extra_disk.vdi']
    end

# App Server 1
    config.vm.define "solr" do |app|
        app.vm.hostname = "solr-vm.test"
        app.vm.network :private_network, ip: "192.168.56.11"
    end
end