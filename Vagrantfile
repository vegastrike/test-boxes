# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
#
#
# Note: This is basically a Ruby Script. Variables and strings can be manipulated
#	in the same was as any Ruby Script.
#

# Selected Networks
base_network_vb = "172.16.12"
base_network_lvt = "172.16.13"

# VM Hardware Resource Configuration
base_memory = 3096
base_cpu_count = 3
base_vram = 128

# 6-month Ubuntu Release
image_ubuntu_latest = "ubuntu/groovy64"

# LTS Ubuntu Releases
image_ubuntu_focal = "ubuntu/focal64"
image_ubuntu_xenial = "ubuntu/xenial64"
image_ubuntu_bionic = "ubuntu/bionic64"

# Select which system to run by setting it to 'true'
# Recommended to only operate one at a time.
system_status_ubuntu_latest = false
system_status_focal = false
system_status_xenial = false
system_status_bionic = true

# Deskto Environment packages by platform
# Package should be  meta-package that install both the Desktop Environment
# and the Login Manager.
debian_desktop_environment = "lubuntu-desktop"

vegastrike_assets_repository = "https://github.com/vegastrike/Assets-Production.git"

# Note: Vagrant tells the VMs to use the UI as this is more of a basic
# VM creation & configuration than testing automation, so the user will
# need to be able to utilize a GUI interface when all is said and one.
Vagrant.configure("2") do |config|

    if system_status_ubuntu_latest then
        config.vm.define "vegastrike_ubuntu_latest" do | vs_ubuntu_latest |
            vs_ubuntu_latest.vm.box = "#{image_ubuntu_latest}"
            vs_ubuntu_latest.vm.network "private_network", ip: "#{base_network_vb}.10"
            vs_ubuntu_latest.vm.hostname = "vegastrike-ubuntu-latest"
            vs_ubuntu_latest.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.gui = true
            end
            vs_ubuntu_latest.vm.provision "shell", inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{debian_desktop_environment}"
                pushd /home/vagrant
                if [ ! -d "Assets-Production" ]; then
                su -c "git clone #{vegastrike_assets_repository}" vagrant
                else
                pushd "Assets-Production"
                su -c "git pull" vagrant
                popd
                fi
                popd
                reboot
            SHELL
        end
    end

    if system_status_focal then
        config.vm.define "vegastrike_ubuntu_focal" do | vs_ubuntu_focal |
            vs_ubuntu_focal.vm.box = "#{image_ubuntu_focal}"
            vs_ubuntu_focal.vm.network "private_network", ip: "#{base_network_vb}.11"
            vs_ubuntu_focal.vm.hostname = "vegastrike-ubuntu-focal"
            vs_ubuntu_focal.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.gui = true
            end
            vs_ubuntu_focal.vm.provision "shell", inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{debian_desktop_environment}"
                pushd /home/vagrant
                if [ ! -d "Assets-Production" ]; then
                su -c "git clone #{vegastrike_assets_repository}" vagrant
                else
                pushd "Assets-Production"
                su -c "git pull" vagrant
                popd
                fi
                popd
                reboot
            SHELL
        end
    end

    if system_status_xenial then
        config.vm.define "vegastrike_ubuntu_xenial" do | vs_ubuntu_xenial |
            vs_ubuntu_xenial.vm.box = "#{image_ubuntu_xenial}"
            vs_ubuntu_xenial.vm.network "private_network", ip: "#{base_network_vb}.12"
            vs_ubuntu_xenial.vm.hostname = "vegastrike-ubuntu-xenial"
            vs_ubuntu_xenial.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.gui = true
            end
            vs_ubuntu_xenial.vm.provision "shell", inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{debian_desktop_environment}"
                pushd /home/vagrant
                if [ ! -d "Assets-Production" ]; then
                su -c "git clone #{vegastrike_assets_repository}" vagrant
                else
                pushd "Assets-Production"
                su -c "git pull" vagrant
                popd
                fi
                popd
                reboot
            SHELL
        end
    end

    if system_status_bionic then
        config.vm.define "vegastrike_ubuntu_bionic" do | vs_ubuntu_bionic |
            vs_ubuntu_bionic.vm.box = "#{image_ubuntu_bionic}"
            vs_ubuntu_bionic.vm.network "private_network", ip: "#{base_network_vb}.13"
            vs_ubuntu_bionic.vm.hostname = "vegastrike-ubuntu-bionic"
            vs_ubuntu_bionic.vm.boot_timeout = 600
            vs_ubuntu_bionic.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.gui = true
            end
            vs_ubuntu_bionic.vm.provision "shell", inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{debian_desktop_environment}" virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
                pushd /home/vagrant
                if [ ! -d "Assets-Production" ]; then
                su -c "git clone #{vegastrike_assets_repository}" vagrant
                else
                pushd "Assets-Production"
                su -c "git pull" vagrant
                popd
                fi
                popd
                reboot
            SHELL
        end
    end

end
