# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<SCRIPT
set -e

if [ ! -x /usr/bin/etcd ] ; then
    cd /tmp/
    curl -L https://github.com/coreos/etcd/releases/download/v2.0.0-rc.1/etcd-v2.0.0-rc.1-linux-amd64.tar.gz -o etcd-v2.0.0-rc.1-linux-amd64.tar.gz
    tar xzvf etcd-v2.0.0-rc.1-linux-amd64.tar.gz
    cd etcd-v2.0.0-rc.1-linux-amd64
    mv etcd /usr/bin/etcd
    mv etcdctl /usr/bin/etcdctl
fi

if [ ! -x /usr/bin/confd ] ; then
    cd /tmp/
    curl -L -O https://github.com/kelseyhightower/confd/releases/download/v0.6.3/confd-0.6.3-linux-amd64
    mv confd-0.6.3-linux-amd64 /usr/bin/confd
    chmod +x /usr/bin/confd
fi

SCRIPT

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/centos-7.0"
  config.ssh.forward_agent = true
  config.vm.provision "shell", inline: $script
end
