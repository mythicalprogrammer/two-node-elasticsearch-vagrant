# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.berkshelf.enabled = true

  config.vm.define :es1 do |es1|
    es1.vm.network :private_network, ip: "192.168.1.10"
    es1.vm.provision :shell, inline: "apt-get update"
    es1.vm.provision :shell, inline:  "gem install chef --version 11.4.2 --no-rdoc --no-ri --conservative"

    es1.vm.provision :chef_solo do |chef|
      chef.add_recipe "java"
      chef.json = {
        java: {
          install_flavor: "oracle",
          jdk_version: "7",
          oracle:  {
                accept_oracle_download_terms: true
          }
        }
      }
    end
    es1.vm.provision :shell, inline:  "wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-0.90.6.deb"
    es1.vm.provision :shell, inline:  "dpkg -i elasticsearch-0.90.6.deb"
  end

  config.vm.define :es2 do |es2|
    es2.vm.network :private_network, ip: "192.168.1.11"
    es2.vm.provision :shell, inline: "apt-get update"
    es2.vm.provision :shell, inline:  "gem install chef --version 11.4.2 --no-rdoc --no-ri --conservative"

    es2.vm.provision :chef_solo do |chef|
      chef.add_recipe "java"
      chef.json = {
        java:  {
          install_flavor: "oracle",
          jdk_version: "7",
          oracle: {
            accept_oracle_download_terms: true
          }
        }
      }
    end
    es2.vm.provision :shell, inline: "wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-0.90.6.deb"
    es2.vm.provision :shell, inline:  "dpkg -i elasticsearch-0.90.6.deb"
  end

end
