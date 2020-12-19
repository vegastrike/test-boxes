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

# Select which system to run by setting it to 'true'
# Recommended to only operate one at a time.
system_status_ubuntu_latest = false
system_status_focal = false
system_status_bionic = false
system_status_xenial = false
system_status_buster = true
system_status_stretch = false

# Select whether or not to clone the Assets-Production repo as part of provisioning
clone_game_assets = false

# Selected Networks
base_network_vb = "172.16.12"
base_network_lvt = "172.16.13"

# VM Hardware Resource Configuration
base_memory = 3096
base_cpu_count = 2
base_vram = 128

# 6-month Ubuntu Release
image_ubuntu_latest = "ubuntu/groovy64"

# LTS Ubuntu Releases
image_ubuntu_focal = "ubuntu/focal64"
image_ubuntu_bionic = "ubuntu/bionic64"
image_ubuntu_xenial = "ubuntu/xenial64"

# Debian Releases
image_debian_buster = "debian/buster64"
image_debian_stretch = "debian/stretch64"

# Deskto Environment packages by platform
# Package should be  meta-package that install both the Desktop Environment
# and the Login Manager.
ubuntu_desktop_environment = "lubuntu-desktop"
debian_desktop_environment = "gnome"

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
            vs_ubuntu_latest.vm.boot_timeout = 900
            vs_ubuntu_latest.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--ostype", "Ubuntu_64"]
                vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
                vb.customize ["modifyvm", :id, "--pae", "on"]
                vb.customize ["modifyvm", :id, "--nestedpaging", "on"]
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
                vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
                vb.customize ["modifyvm", :id, "--audioout", "on"]
                vb.gui = true
            end
            vs_ubuntu_latest.vm.provision "shell", privileged: true, inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{ubuntu_desktop_environment}" virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
            SHELL
            if clone_game_assets then
                vs_ubuntu_latest.vm.provision "shell", privileged: false, inline: <<-SHELL
                    pushd /home/vagrant
                    if [ ! -d "Assets-Production" ]; then
                        git clone #{vegastrike_assets_repository}
                    else
                        pushd "Assets-Production"
                        git pull
                        popd
                    fi
                    popd
                SHELL
            end
            vs_ubuntu_latest.vm.provision "shell", privileged: true, inline: <<-SHELL
                reboot
            SHELL
        end
    end

    if system_status_focal then
        config.vm.define "vegastrike_ubuntu_focal" do | vs_ubuntu_focal |
            vs_ubuntu_focal.vm.box = "#{image_ubuntu_focal}"
            vs_ubuntu_focal.vm.network "private_network", ip: "#{base_network_vb}.11"
            vs_ubuntu_focal.vm.hostname = "vegastrike-ubuntu-focal"
            vs_ubuntu_focal.vm.boot_timeout = 900
            vs_ubuntu_focal.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--ostype", "Ubuntu_64"]
                vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
                vb.customize ["modifyvm", :id, "--pae", "on"]
                vb.customize ["modifyvm", :id, "--nestedpaging", "on"]
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
                vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
                vb.customize ["modifyvm", :id, "--audioout", "on"]
                vb.gui = true
            end
            vs_ubuntu_focal.vm.provision "shell", privileged: true, inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{ubuntu_desktop_environment}" virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
            SHELL
            if clone_game_assets then
                vs_ubuntu_focal.vm.provision "shell", privileged: false, inline: <<-SHELL
                    pushd /home/vagrant
                    if [ ! -d "Assets-Production" ]; then
                        git clone #{vegastrike_assets_repository}
                    else
                        pushd "Assets-Production"
                        git pull
                        popd
                    fi
                    popd
                SHELL
            end
            vs_ubuntu_focal.vm.provision "shell", privileged: true, inline: <<-SHELL
                reboot
            SHELL
        end
    end

    if system_status_bionic then
        config.vm.define "vegastrike_ubuntu_bionic" do | vs_ubuntu_bionic |
            vs_ubuntu_bionic.vm.box = "#{image_ubuntu_bionic}"
            vs_ubuntu_bionic.vm.network "private_network", ip: "#{base_network_vb}.13"
            vs_ubuntu_bionic.vm.hostname = "vegastrike-ubuntu-bionic"
            vs_ubuntu_bionic.vm.boot_timeout = 900
            vs_ubuntu_bionic.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--ostype", "Ubuntu_64"]
                vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
                vb.customize ["modifyvm", :id, "--pae", "on"]
                vb.customize ["modifyvm", :id, "--nestedpaging", "on"]
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
                vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
                vb.customize ["modifyvm", :id, "--audioout", "on"]
                vb.gui = true
            end
            vs_ubuntu_bionic.vm.provision "shell", privileged: true, inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{ubuntu_desktop_environment}" virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
            SHELL
            if clone_game_assets then
                vs_ubuntu_bionic.vm.provision "shell", privileged: false, inline: <<-SHELL
                    pushd /home/vagrant
                    if [ ! -d "Assets-Production" ]; then
                        git clone #{vegastrike_assets_repository}
                    else
                        pushd "Assets-Production"
                        git pull
                        popd
                    fi
                    popd
                SHELL
            end
            vs_ubuntu_bionic.vm.provision "shell", privileged: true, inline: <<-SHELL
                reboot
            SHELL
        end
    end

    if system_status_xenial then
        config.vm.define "vegastrike_ubuntu_xenial" do | vs_ubuntu_xenial |
            vs_ubuntu_xenial.vm.box = "#{image_ubuntu_xenial}"
            vs_ubuntu_xenial.vm.network "private_network", ip: "#{base_network_vb}.12"
            vs_ubuntu_xenial.vm.hostname = "vegastrike-ubuntu-xenial"
            vs_ubuntu_xenial.vm.boot_timeout = 900
            vs_ubuntu_xenial.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--ostype", "Ubuntu_64"]
                vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
                vb.customize ["modifyvm", :id, "--pae", "on"]
                vb.customize ["modifyvm", :id, "--nestedpaging", "on"]
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
                vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
                vb.customize ["modifyvm", :id, "--audioout", "on"]
                vb.gui = true
            end
            vs_ubuntu_xenial.vm.provision "shell", privileged: true, inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{ubuntu_desktop_environment}" virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11
            SHELL
            if clone_game_assets then
                vs_ubuntu_xenial.vm.provision "shell", privileged: false, inline: <<-SHELL
                    pushd /home/vagrant
                    if [ ! -d "Assets-Production" ]; then
                        git clone #{vegastrike_assets_repository}
                    else
                        pushd "Assets-Production"
                        git pull
                        popd
                    fi
                    popd
                SHELL
            end
            vs_ubuntu_xenial.vm.provision "shell", privileged: true, inline: <<-SHELL
                reboot
            SHELL
        end
    end

    if system_status_buster then
        config.vm.define "vegastrike_debian_buster" do | vs_debian_buster |
            vs_debian_buster.vm.box = "#{image_debian_buster}"
            vs_debian_buster.vm.network "private_network", ip: "#{base_network_vb}.14"
            vs_debian_buster.vm.hostname = "vegastrike-debian-buster"
            vs_debian_buster.vm.boot_timeout = 900
            vs_debian_buster.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--ostype", "Debian_64"]
                vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
                vb.customize ["modifyvm", :id, "--pae", "on"]
                vb.customize ["modifyvm", :id, "--nestedpaging", "on"]
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
                vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
                vb.customize ["modifyvm", :id, "--audioout", "on"]
                vb.gui = true
            end
            vs_debian_buster.vm.provision "shell", privileged: true, inline: <<-SHELL
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{debian_desktop_environment}"
            SHELL
            if clone_game_assets then
                vs_debian_buster.vm.provision "shell", privileged: false, inline: <<-SHELL
                    pushd /home/vagrant
                    if [ ! -d "Assets-Production" ]; then
                        git clone #{vegastrike_assets_repository}
                    else
                        pushd "Assets-Production"
                        git pull
                        popd
                    fi
                    popd
                SHELL
            end
            vs_debian_buster.vm.provision "shell", privileged: true, inline: <<-SHELL
                reboot
            SHELL
        end
    end

    if system_status_stretch then
        config.vm.define "vegastrike_debian_stretch" do | vs_debian_stretch |
            vs_debian_stretch.vm.box = "#{image_debian_stretch}"
            vs_debian_stretch.vm.network "private_network", ip: "#{base_network_vb}.15"
            vs_debian_stretch.vm.hostname = "vegastrike-debian-stretch"
            vs_debian_stretch.vm.boot_timeout = 900
            vs_debian_stretch.vm.provider "virtualbox" do |vb|
                vb.memory = "#{base_memory}"
                vb.cpus = "#{base_cpu_count}"
                vb.customize ["modifyvm", :id, "--ostype", "Debian_64"]
                vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
                vb.customize ["modifyvm", :id, "--pae", "on"]
                vb.customize ["modifyvm", :id, "--nestedpaging", "on"]
                vb.customize ["modifyvm", :id, "--vram", "#{base_vram}"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
                vb.customize ["modifyvm", :id, "--accelerate2dvideo", "on"]
                vb.customize ["modifyvm", :id, "--audioout", "on"]
                vb.gui = true
            end
            vs_debian_stretch.vm.provision "shell", privileged: true, inline: <<-SHELL
                echo "deb http://deb.debian.org/debian stretch-backports contrib main" | tee /etc/apt/sources.list.d/stretch-backports.list
                apt-get update
                apt-get install -y ansible python-apt
                apt-get install -y git
                apt-get install -y "#{debian_desktop_environment}"
                apt-get install -y linux-image-amd64 linux-headers-amd64 -t stretch-backports
                apt-get install -y virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11 -t stretch-backports
            SHELL
            if clone_game_assets then
                vs_debian_stretch.vm.provision "shell", privileged: false, inline: <<-SHELL
                    pushd /home/vagrant
                    if [ ! -d "Assets-Production" ]; then
                        git clone #{vegastrike_assets_repository}
                    else
                        pushd "Assets-Production"
                        git pull
                        popd
                    fi
                    popd
                SHELL
            end
            vs_debian_stretch.vm.provision "shell", privileged: true, inline: <<-SHELL
                reboot
            SHELL
        end
    end

end
