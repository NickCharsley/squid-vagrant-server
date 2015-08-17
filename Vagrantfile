# Configuration file to spin up a machine that will act as HTTP proxy and cache apt-get installations
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.hostname = "squid-cache"

  # Create a host-only network to the vagrant instance.
  config.vm.network :private_network, ip: "10.0.0.10"

  # Do not use the cache. I am the cache.
  if Vagrant.has_plugin?('vagrant-proxyconf')
    config.proxy.enabled = false
  end

  # Extra RAM
  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    # Virtualbox Custom CPU count:
    vb.customize ["modifyvm", :id, "--name", "cache"]
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # Install squid-deb-proxy server.
  $script = <<SCRIPT
apt-get update
apt-get install -y squid
apt-get install -y squid-deb-proxy
apt-get install -y language-pack-en
cp /vagrant/squid.conf /etc/squid3/squid.conf
service squid3 restart
SCRIPT

  config.vm.provision :shell, :inline => $script

end
