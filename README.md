#Vagrant Configuration for Multi-Machine WireGuard Setup
This Vagrant configuration provides a simple way to set up a multi-machine WireGuard network for development purposes. It includes three Fedora ARM64 machines and one Ubuntu ARM machine, each with WireGuard installed and configured.

#Prerequisites
Before you begin, ensure that you have the following software installed on your system:

1Vagrant
2VMware Desktop Vagrant Provider

#Usage
Clone this repository to your local machine:


git clone [repository_url]
Change into the cloned directory:


cd [repository_directory]
Start the virtual machines:


vagrant up
Access the virtual machines:


vagrant ssh [machine_name]

#Machines
1. scriptbox
Box: jacobw/fedora35-arm64
IP Address: 192.168.56.26
Hostname: scriptbox
2. web01
Box: jacobw/fedora35-arm64
IP Address: 192.168.56.27
Hostname: web01
3. web02
Box: jacobw/fedora35-arm64
IP Address: 192.168.56.28
Hostname: web02
4. web03
Box: spox/ubuntu-arm (version 1.0.0)
IP Address: 192.168.56.29
Hostname: web03
WireGuard Configuration
WireGuard is installed on each machine with the following configuration:

PrivateKey and PublicKey are generated and stored in /etc/wireguard/.
WireGuard interface (wg0) is configured with a unique IP address and port for each machine.
#Notes
The virtual machines are configured to use the VMware Desktop provider. Ensure that you have the provider installed and properly configured.

The Vagrant script includes provisions to install WireGuard, update the package manager, and configure the WireGuard interface.

The firewalld service is stopped during provisioning to avoid interference with WireGuard.

GUI is enabled for each machine to allow easy interaction via a graphical interface.

#Contributing
Feel free to contribute to this project by submitting issues or pull requests. Your feedback is valuable!
