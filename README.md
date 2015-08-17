## Virtual Squid3 Proxy Server

Execute `vagrant up` to launch a private Squid proxy server at 10.0.0.10:3983. It also runs squid-deb-proxy at 10.0.0.10:8080.

#### Routing Vagrant machines through the proxy

* Install the Vagrant proxy plugin:
  * `vagrant plugin install vagrant-proxyconf`
* Copy the `global_Vagrantfile` to the global config directory to affect all Vagrantfiles everywhere:
  * `cp global_Vagrantfile ~/.vagrant.d/Vagrantfile`

