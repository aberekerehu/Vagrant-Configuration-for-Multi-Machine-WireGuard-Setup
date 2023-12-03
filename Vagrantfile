Vagrant.configure("2") do |config|
  config.vm.define "scriptbox" do |scriptbox|
    scriptbox.vm.box = "jacobw/fedora35-arm64"
    scriptbox.vm.network "private_network", ip: "192.168.56.26"
    scriptbox.vm.hostname = "scriptbox"
    scriptbox.vm.provider "vmware_desktop" do |v|
      v.allowlist_verified = true
      v.ssh_info_public = true
      v.gui = true
    end
    scriptbox.vm.provision "shell", inline: <<-SHELL
      sudo dnf install -y wireguard-tools
      mv /etc/yum.repos.d/fedora-updates.repo /tmp/
      mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
      yum clean all
      yum update
      systemctl stop firewalld
      # Configure WireGuard
      sudo wg genkey | sudo tee /etc/wireguard/privatekey | wg pubkey | sudo tee /etc/wireguard/publickey
      sudo bash -c 'cat <<EOF > /etc/wireguard/wg0.conf
      [Interface]
      PrivateKey = $(cat /etc/wireguard/privatekey)
      Address = 192.168.56.26/24
      ListenPort = 51820
EOF'
      sudo systemctl enable wg-quick@wg0
      sudo systemctl start wg-quick@wg0
    SHELL
  end

  config.vm.define "web01" do |web01|
    web01.vm.box = "jacobw/fedora35-arm64"
    web01.vm.network "private_network", ip: "192.168.56.27"
    web01.vm.hostname = "web01"
    web01.vm.provider "vmware_desktop" do |v|
      v.allowlist_verified = true
      v.ssh_info_public = true
      v.gui = true
    end
    web01.vm.provision "shell", inline: <<-SHELL
      # Install WireGuard on Fedora
      sudo dnf install -y wireguard-tools
      mv /etc/yum.repos.d/fedora-updates.repo /tmp/
      mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
      yum clean all
      yum update
      systemctl stop firewalld
      # Configure WireGuard
      sudo wg genkey | sudo tee /etc/wireguard/privatekey | wg pubkey | sudo tee /etc/wireguard/publickey
      sudo bash -c 'cat <<EOF > /etc/wireguard/wg0.conf
      [Interface]
      PrivateKey = $(cat /etc/wireguard/privatekey)
      Address = 192.168.56.27/24
      ListenPort = 51820
EOF'
      sudo systemctl enable wg-quick@wg0
      sudo systemctl start wg-quick@wg0
    SHELL
  end

  config.vm.define "web02" do |web02|
    web02.vm.box = "jacobw/fedora35-arm64"
    web02.vm.network "private_network", ip: "192.168.56.28"
    web02.vm.hostname = "web02"
    web02.vm.provider "vmware_desktop" do |v|
      v.allowlist_verified = true
      v.ssh_info_public = true
      v.gui = true
    end
    web02.vm.provision "shell", inline: <<-SHELL
      # Install WireGuard on Fedora
      sudo dnf install -y wireguard-tools
      mv /etc/yum.repos.d/fedora-updates.repo /tmp/
      mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
      yum clean all
      yum update
      systemctl stop firewalld
      # Configure WireGuard
      sudo wg genkey | sudo tee /etc/wireguard/privatekey | wg pubkey | sudo tee /etc/wireguard/publickey
      sudo bash -c 'cat <<EOF > /etc/wireguard/wg0.conf
      [Interface]
      PrivateKey = $(cat /etc/wireguard/privatekey)
      Address = 192.168.56.28/24
      ListenPort = 51820
EOF'
      sudo systemctl enable wg-quick@wg0
      sudo systemctl start wg-quick@wg0
    SHELL
  end

  config.vm.define "web03" do |web03|
    web03.vm.box = "spox/ubuntu-arm"
    web03.vm.box_version = "1.0.0"
    web03.vm.network "private_network", ip: "192.168.56.29"
    web03.vm.hostname = "web03"
    web03.vm.provider "vmware_desktop" do |v|
      v.allowlist_verified = true
      v.ssh_info_public = true
      v.gui = true
    end
    web03.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y wireguard

      # Configure WireGuard
      sudo wg genkey | sudo tee /etc/wireguard/privatekey | wg pubkey | sudo tee /etc/wireguard/publickey
      sudo bash -c 'cat <<EOF > /etc/wireguard/wg0.conf
      [Interface]
      PrivateKey = $(cat /etc/wireguard/privatekey)
      Address = 192.168.56.29/24
      ListenPort = 51820
EOF'
      sudo systemctl enable wg-quick@wg0
      sudo systemctl start wg-quick@wg0
    SHELL
  end
end

