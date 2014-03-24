# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :centos64_64 do |cfg|
    cfg.vm.box = "centos64-x86_64"
    cfg.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20131103.box"
    cfg.vm.box_download_checksum_type = "sha256"
    cfg.vm.box_download_checksum = "e57a14fb73af0d98084411581f86e190590944f8d2120d2d89fefb85066aa622"
  end

  config.vm.define :centos64_32 do |cfg|
    cfg.vm.box = "centos64-i386"
    cfg.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-i386-v20131103.box"
    cfg.vm.box_download_checksum_type = "sha256"
    cfg.vm.box_download_checksum = "d04663cdc0300c06325b87bbb8cc95750d953892dcb953c142fdca553a10be43"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.verbose = "v"
    ansible.groups = {
      "app" => ["centos64_64"],
      "db" => ["centos64_64"],
      "session" => ["centos64_64"]
    }
    if File.exist?("local_vars.yml")
      ansible.extra_vars = "local_vars.yml"
    end
  end
end
