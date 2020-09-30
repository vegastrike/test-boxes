Vega Strike VM Testing
======================

This repository provides a series of Virtual Machines avialable to the user for testing the Vega Strike binaries.
Each Virtaul Machine when fully configured will have the game asset data and be ready for the user to do an install of the Vega Strike Packaging.

The Virtual Machines are standard virtual machines without anything special done. When the Virtual Machine is brought up the VM GUI application will be provided to the user.

Requirements
------------

* VirtualBox
* Minimum 2GB RAM for the Virtual Machines
* Minimum 2 CPU Cores available for the Virtual Machines

.. note:: Support for libvirt is provided for the Network and minimal effort could be done to support libvirt images.


Credentials
-----------

The Virtual Machines should use the standard Vagrant User and Password:

.. code-block: yaml

    user: vagrant
    password: vagrant

Selecting a Desktop
-------------------

By default the Virtual Machines will install the LXDE desktop on any Linux Virtual Machines.
This can be changed by editing the `desktop_environment` variable in the Vagrantfile.
Please ensure to use the appropriate package name to install the complete desktop environment and login management.

LXDE was selected as the default as it uses fewer resources allowing the Virtual Machine to operate with less RAM.


Machine Configuration
---------------------

By default the Virtual Machine has 2 GB of RAM and 2 Processor Nodes.
This can be changed by editing the `base_memory` and `base_cpu_count` respectively in the Vagrantfile.

Network
-------

Vega Strike does not at this time require a network configuration.
However, as the installation will require the user to download the appropriate package file and manually
install it a network configuration is still provided.

The Vagrantfile currently supports both libvirt and Virtual Box images even though only it only uses Virtual Box images.

The following IP blocks are reserved for use:

* 172.16.12.0/24 - Virtual Box Networking
* 172.16.13.0/24 - LibVirt Networking

Vagrant and Virtual Machine Hypervisors typically reserver some IPs for their own use.
For this reason the first machine will use the `.10` address (e.g. `172.16.12.10`) and
each following machine will increment from there.

.. note:: The IP addresses are currently hard-coded to the machine and only flexible in the IP block they are assigned to.

