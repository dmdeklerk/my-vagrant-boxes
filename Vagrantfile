# -*- mode: ruby -*-
# vi: set ft=ruby :

#
# Vagrant file for creating a vm that is later used to create a base box
# contains things like ruby, rbenv, bundler, mysql. Things that just take
# to long to build each time you do a test run.
#

Vagrant.configure('2') do |config|

  config.vm.box                 = "canonical-ubuntu-12.04"
  config.vm.box_url             = "http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-i386-vagrant-disk1.box"
  config.omnibus.chef_version   = :latest
  config.vm.boot_timeout        = 120
  config.berkshelf.enabled      = true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
  end

  config.vm.define 'rbenv-1.9.3-p448' do |box|
    config.vm.provision "chef_solo" do |chef|
      chef.add_recipe "my-vagrant-boxes::rbenv-1.9.3-p448"
    end
  end

end
