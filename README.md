## Virtual Squid3 Proxy Server

Execute `vagrant up` to launch a private Squid proxy server at 10.0.0.10:3983. It also runs squid-deb-proxy at 10.0.0.10:8080.

Copy the `global_Vagrantfile` into Vagrant's global config directory to have all machines route their requests through the proxy.

    cp global_Vagrantfile ~/.vagrant.d/Vagrantfile
