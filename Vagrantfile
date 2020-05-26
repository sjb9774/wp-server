
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: '10.19.90.99'
  config.vm.synced_folder "/Users/stephen.biston/git/stephenbiston.com", "/srv/website", type: "nfs"
  # simple provision to allow us to ssh as vagrant using of the keys used in the
  # playbook; usually vagrant sets up its own key for the vagrant user but for
  # simplicity (and for the closest functional mirroring of AWS instances) we
  # want to be able to use the same key to access all the users -- this
  # essentially mimics setting up a keypair for the centos user on AWS
  # config.vm.provision "shell", inline: <<-SHELL
  #   for f in /vagrant/files/ssh/*
  #   do
  #     cat $f >> /home/vagrant/.ssh/authorized_keys
  #   done
  # SHELL
  config.vm.define "wp_dev" do |web|
    web.vm.provider :virtualbox do |vb|
      vb.name = "wp_dev"
    end
  end
end
