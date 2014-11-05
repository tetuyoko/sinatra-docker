VAGRANTFILE_API_VERSION = "2"

BASE_BOX_URL    = ENV['BASE_BOX_URL'] || 'https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/'
VAGRANT_BOX_URL = ENV['VAGRANT_BOX_URL'] || BASE_BOX_URL + 'ubuntu-14.04-amd64-vbox.box'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "phusion-open-ubuntu-14.04-amd64"
  config.vm.box_url = VAGRANT_BOX_URL 
  config.ssh.forward_agent = true

  config.vm.network :forwarded_port, guest: 4567, host: 4567
  config.vm.provision :docker do |d|
    d.pull_images "ubuntu"
  end
end
