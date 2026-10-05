CODIGO = "2226090"

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  # ---------- SERVIDOR 1: firewall UFW ----------
  config.vm.define "srv1" do |s|
    s.vm.hostname = "srv1-#{CODIGO}"
    s.vm.network "private_network", ip: "192.168.56.10"                       # red pública
    s.vm.network "private_network", ip: "192.168.50.1",
                 virtualbox__intnet: "red_interna"                            # red interna
    s.vm.provider "virtualbox" do |vb|
      vb.name = "srv1-#{CODIGO}"
      vb.memory = 1024
    end
  end

  # ---------- SERVIDOR 2: vsftpd / sshd ----------
  config.vm.define "srv2" do |s|
    s.vm.hostname = "srv2-#{CODIGO}"
    s.vm.network "private_network", ip: "192.168.50.2",
                 virtualbox__intnet: "red_interna"                            # solo red interna
    s.vm.provider "virtualbox" do |vb|
      vb.name = "srv2-#{CODIGO}"
      vb.memory = 1024
    end
  end

  # ---------- CLIENTE ----------
  config.vm.define "cliente" do |c|
    c.vm.hostname = "cliente-#{CODIGO}"
    c.vm.network "private_network", ip: "192.168.56.20"                       # solo red pública
    c.vm.provider "virtualbox" do |vb|
      vb.name = "cliente-#{CODIGO}"
      vb.memory = 1024
    end
  end
end